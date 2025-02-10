# Filter Data Dynamically

![ScreenRecording2025-02-10at9 13 33PM-ezgif com-video-to-gif-converter](https://github.com/user-attachments/assets/38fddcd2-50b9-4347-af99-46425b82929a)


**Approach:**

- Change Filter Data based on Search State.
- Due to Use State, It updating filterData again.

- **App.jsx**

```jsx
import { useState } from "react";
import { data } from "./data";

const App = () => {
  const [search, setSearch] = useState("");

  const filteredData = search
    ? data.filter(
        (item) =>
          item.first_name.toLowerCase().includes(search.toLowerCase()) ||
          item.last_name.toLowerCase().includes(search.toLowerCase()) ||
          item.email.toLowerCase().includes(search.toLowerCase()) ||
          item.phone.includes(search)
      )
    : data;

  return (
    <div className="container mx-auto">
      <h1 className="text-3xl text-center my-5">Contact Keeper</h1>
      <div>
        <input
          className="w-full border border-slate-200 outline-none p-2 px-3 rounded"
          type="text"
          placeholder="Search Here"
          value={search}
          onChange={(e) => setSearch(e.target.value)}
        />
      </div>

      <div className="overflow-x-auto mt-7">
        <table className="min-w-full border border-gray-300 bg-white shadow-md rounded-lg">
          <thead className="bg-gray-100">
            <tr>
              <th className="px-4 py-2 border-b text-left text-gray-600">
                First Name
              </th>
              <th className="px-4 py-2 border-b text-left text-gray-600">
                Last Name
              </th>
              <th className="px-4 py-2 border-b text-left text-gray-600">
                Email
              </th>
              <th className="px-4 py-2 border-b text-left text-gray-600">
                Phone
              </th>
            </tr>
          </thead>
          <tbody>
            {filteredData.length > 0 ? (
              filteredData.map((contact) => {
                return (
                  <tr key={contact.id}>
                    <td className="px-4 py-2 border-b text-left text-gray-600">
                      {contact.first_name}
                    </td>
                    <td className="px-4 py-2 border-b text-left text-gray-600">
                      {contact.last_name}
                    </td>
                    <td className="px-4 py-2 border-b text-left text-gray-600">
                      {contact.email}
                    </td>
                    <td className="px-4 py-2 border-b text-left text-gray-600">
                      {contact.phone}
                    </td>
                  </tr>
                );
              })
            ) : (
              <tr>
                <td colSpan="4" className="px-4 py-2 text-center text-gray-500">
                  No results found
                </td>
              </tr>
            )}
          </tbody>
        </table>
      </div>
    </div>
  );
};

export default App;

```
