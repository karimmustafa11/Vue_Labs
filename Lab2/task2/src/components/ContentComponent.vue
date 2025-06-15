<template>
    <div style="flex: 1;">
        <table border="1" style="width: 100%; text-align: center; border-collapse: collapse;">
            <thead>
                <tr>
                    <th>ID</th>
                    <th>Name</th>
                    <th>City</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="student in students" :key="student.id">
                    <td>{{ student.id }}</td>
                    <td>{{ student.name }}</td>
                    <td>{{ student.city }}</td>
                </tr>
            </tbody>
            <tfoot>
                
                    
            </tfoot>
        </table>
    </div>
</template>

<script>
export default {
    data() {
        return {
            students: [
                { id: 100, name: 'Mario', city: 'Assiut' },
                { id: 200, name: 'Abd el rahman', city: 'Cairo' },
                { id: 300, name: 'Islam', city: 'Alexandria' },
                { id: 400, name: 'Gehad', city: 'Minia' },
                { id: 500, name: 'Nourhan', city: 'Aswan' },
            ]
        }
    }
}
</script>