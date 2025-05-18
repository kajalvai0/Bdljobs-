// pages/admin/index.tsx
import { useEffect, useState } from "react";
import { useRouter } from "next/router";
import { supabase } from "../../utils/supabaseClient";

export default function AdminDashboard() {
  const [jobs, setJobs] = useState<any[]>([]);
  const [profiles, setProfiles] = useState<any[]>([]);
  const [stats, setStats] = useState({ jobs: 0, profiles: 0 });
  const router = useRouter();

  useEffect(() => {
    const checkAdmin = async () => {
      const user = supabase.auth.user();
      const { data } = await supabase.from("profiles").select("role").eq("id", user?.id).single();
      if (!user || data?.role !== "admin") {
        router.push("/");
      }
    };

    const fetchData = async () => {
      const { data: jobData } = await supabase.from("jobs").select("*");
      const { data: profileData } = await supabase.from("profiles").select("*");
      setJobs(jobData || []);
      setProfiles(profileData || []);
      setStats({ jobs: jobData?.length || 0, profiles: profileData?.length || 0 });
    };

    checkAdmin();
    fetchData();
  }, [router]);

  const deleteJob = async (id: number) => {
    await supabase.from("jobs").delete().eq("id", id);
    setJobs(jobs.filter((job) => job.id !== id));
  };

  const deleteProfile = async (id: string) => {
    await supabase.from("profiles").delete().eq("id", id);
    setProfiles(profiles.filter((profile) => profile.id !== id));
  };

  const toggleApproval = async (table: string, id: number | string, current: boolean) => {
    await supabase.from(table).update({ approved: !current }).eq("id", id);
    if (table === "jobs") {
      const { data } = await supabase.from("jobs").select("*");
      setJobs(data || []);
    } else {
      const { data } = await supabase.from("profiles").select("*");
      setProfiles(data || []);
    }
  };

  const exportCSV = (data: any[], filename: string) => {
    const headers = Object.keys(data[0] || {}).join(",");
    const rows = data.map(row => Object.values(row).join(",")).join("\n");
    const csv = `${headers}\n${rows}`;
    const blob = new Blob([csv], { type: "text/csv" });
    const url = window.URL.createObjectURL(blob);
    const a = document.createElement("a");
    a.href = url;
    a.download = filename;
    a.click();
    window.URL.revokeObjectURL(url);
  };

  return (
    <div className="p-6">
      <h1 className="text-3xl font-bold mb-4">Admin Dashboard</h1>

      <div className="grid grid-cols-2 gap-4 mb-6">
        <div className="bg-blue-100 p-4 rounded shadow">
          <h3 className="text-xl font-semibold">Total Jobs</h3>
          <p className="text-2xl">{stats.jobs}</p>
        </div>
        <div className="bg-green-100 p-4 rounded shadow">
          <h3 className="text-xl font-semibold">Total Profiles</h3>
          <p className="text-2xl">{stats.profiles}</p>
        </div>
      </div>

      <section className="mb-6">
        <div className="flex justify-between items-center">
          <h2 className="text-xl font-semibold mb-2">Job Listings</h2>
          <button onClick={() => exportCSV(jobs, 'jobs.csv')} className="btn">Export Jobs</button>
        </div>
        <div className="space-y-2">
          {jobs.map((job) => (
            <div key={job.id} className="p-4 bg-white rounded shadow flex justify-between items-center">
              <div>
                <h3 className="font-bold">{job.title}</h3>
                <p>{job.location} — {job.type}</p>
                <p>৳{job.salary}</p>
                <p>Status: <span className={job.approved ? 'text-green-600' : 'text-yellow-600'}>{job.approved ? 'Approved' : 'Pending'}</span></p>
              </div>
              <div className="space-x-2">
                <button onClick={() => toggleApproval("jobs", job.id, job.approved)} className="text-blue-600">{job.approved ? 'Reject' : 'Approve'}</button>
                <button onClick={() => deleteJob(job.id)} className="text-red-600">Delete</button>
              </div>
            </div>
          ))}
        </div>
      </section>

      <section>
        <div className="flex justify-between items-center">
          <h2 className="text-xl font-semibold mb-2">Worker Profiles</h2>
          <button onClick={() => exportCSV(profiles, 'profiles.csv')} className="btn">Export Profiles</button>
        </div>
        <div className="space-y-2">
          {profiles.map((profile) => (
            <div key={profile.id} className="p-4 bg-gray-100 rounded flex justify-between items-center">
              <div>
                <p><strong>Job Type:</strong> {profile.jobType}</p>
                <p><strong>Experience:</strong> {profile.experience}</p>
                <p><strong>Availability:</strong> {profile.availability}</p>
                <p><strong>Salary:</strong> ৳{profile.salary}</p>
                <p>Status: <span className={profile.approved ? 'text-green-600' : 'text-yellow-600'}>{profile.approved ? 'Approved' : 'Pending'}</span></p>
              </div>
              <div className="space-x-2">
                <button onClick={() => toggleApproval("profiles", profile.id, profile.approved)} className="text-blue-600">{profile.approved ? 'Reject' : 'Approve'}</button>
                <button onClick={() => deleteProfile(profile.id)} className="text-red-600">Delete</button>
              </div>
            </div>
          ))}
        </div>
      </section>
    </div>
  );
}
