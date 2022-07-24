<script>
export default {

    name: 'OpenOrder',
    data() {
        return {
            fetched: false,
            data: [
                {
                    "ps_no": 8582568,
                    "po_no": "TEST BO TRG",
                    "date": "7/14/22",
                    "entryloc": "HBL",
                    "shiploc": "HBL",
                    "total": 17.26,
                    "asc": 999,
                    "status": "B/O"
                },
                {
                    "ps_no": 8582128,
                    "po_no": "TEST BO TRG",
                    "date": "7/12/22",
                    "entryloc": "HBL",
                    "shiploc": "ELK",
                    "total": 74.08,
                    "asc": 999,
                    "status": "QUEUED"
                },
                {
                    "ps_no": 8582115,
                    "po_no": "TEST TRG CNT",
                    "date": "7/12/22",
                    "entryloc": "HBL",
                    "shiploc": "ELK",
                    "total": 1.86,
                    "asc": 999,
                    "status": "QUEUED"
                },
                {
                    "ps_no": 8582094,
                    "po_no": "TEST OSOD",
                    "date": "7/12/22",
                    "entryloc": "HBL",
                    "shiploc": "HBL",
                    "total": 10.23,
                    "asc": 999,
                    "status": "QUEUED"
                }
            ],
            headerNames: [
                'P/S No.',
                'PO Number',
                'Date',
                'Entry Loc',
                'Ship Loc',
                'Total',
                'Asc',
                'Status'
            ]
        }
    }
}
</script>
<template>
    <div id="open-order">
        <div class="filterBar">
            <div id="status">
                <p class="filter-caption">STATUS</p>
                <span>
                    <p class="filter-option">B/O</p>
                    <p class="items">1</p>
                </span>
                <span>
                    <p class="filter-option">Queued</p>
                    <p class="items">3</p>
                </span>
            </div>
            <div id="entry-location">
                <p class="filter-caption">ENTRY LOCATION</p>
                <span>
                    <p class="filter-option">HBL</p>
                    <p class="items">4</p>
                </span>
                <span>
                    <p class="filter-option">ELK</p>
                    <p class="items">0</p>
                </span>
            </div>
        </div>
        <table>
            <tr>
                <th v-for="name in headerNames" v-bind:key="name">{{ name }}</th>
            </tr>
            <tr v-for="row in data" v-bind:key="row.ps_no">
                <td>{{ row.ps_no }}</td>
                <td>{{ row.po_no }}</td>
                <td>{{ row.date }}</td>
                <td>{{ row.entryloc }}</td>
                <td>{{ row.shiploc }}</td>
                <td>{{ row.total }}</td>
                <td>{{ row.asc }}</td>
                <td>{{ row.status }}</td>
            </tr>
        </table>

    </div>
</template>
<style scoped>
* {
    font-family: 'Open Sans', sans-serif;
}

table {
    width: 70%;
    border-spacing: 0;
    border-collapse: collapse;
}

th {
    text-align: left;
    color: white;
    background-color: #666667;
    padding: 5px;
    border: 1px solid white;
}

td {
    border: 1px solid #666667;
    padding: 5px;
}

#open-order {
    display: flex;
    height: 100%;
    align-items: flex-start;
    justify-content: space-between;
}

.filterBar {
    box-shadow: rgb(0, 0, 0, 0.25) 5px 0px 10px;
    width: 25%;
    align-self: stretch;
    padding: 10px;
}

.filter-caption {
    font-size: 1rem;
    color: #666667;

}

.filterBar span {
    display: flex;
    align-items: center;
}

.filter-option {
    font-size: 0.9rem;
    margin-left: 1rem;
}

.items {
    font-size: 0.9rem;
    padding: 2px 5px;
    border: 1px solid #e5e5e5;
    margin-left: 5px;
}
</style>