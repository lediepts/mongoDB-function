# mongoDB-function

- Insert many
```js:
db.inventory.insertMany([
   // MongoDB adds the _id field with an ObjectId if _id is not present
   { item: "journal", qty: 25, status: "A",
       size: { h: 14, w: 21, uom: "cm" }, tags: [ "blank", "red" ] },
   { item: "notebook", qty: 50, status: "A",
       size: { h: 8.5, w: 11, uom: "in" }, tags: [ "red", "blank" ] },
   { item: "paper", qty: 100, status: "D",
       size: { h: 8.5, w: 11, uom: "in" }, tags: [ "red", "blank", "plain" ] },
   { item: "planner", qty: 75, status: "D",
       size: { h: 22.85, w: 30, uom: "cm" }, tags: [ "blank", "red" ] },
   { item: "postcard", qty: 45, status: "A",
       size: { h: 10, w: 15.25, uom: "cm" }, tags: [ "blue" ] }
]);
```
- Các mode khi sort với Mongodb lần lượt là: 1(tăng dần) và -1(giảm dần) thay vì esc và desc trong mysql
- Aggregation có thể hiểu là sự tập hợp. Các Aggregation operation xử lý các bản ghi dữ liệu và trả về kết quả đã được tính toán. Các phép toán tập hợp nhóm các giá trị từ nhiều Document lại với nhau, và có thể thực hiện nhiều phép toán đa dạng trên dữ liệu đã được nhóm đó để trả về một kết quả duy nhất. Trong SQL, count() và GROUP BY là tương đương với Aggregation trong MongoDB, cú pháp:
```js:
db.COLLECTION_NAME.aggregate(AGGREGATE_OPERATION)
```
  - ex:
  ![ex](/images/2.jpg)
- Map-Reduce là một hệ xử lý dữ liệu để cô đọng một khối lượng lớn dữ liệu thành các kết quả tổng thể có ích. MongoDB sử dụng lệnh mapReduce cho hoạt động Map-Reduce. Nói chung, Map Reduce được sử dụng để xử lý các tập dữ liệu lớn.
```js:
db.collection.mapReduce(
       function() {emit(key,value);},  //map function
       function(key,values) {return reduceFunction},   //reduce function
       {
          out: collection,
          query: document,
          sort: document,
          limit: number
       }
    )
```
    - map là một hàm JavaScript mà ánh xạ một value với một key và phát xạ một cặp key-value.
    - reduce là một hàm JavaScript mà rút gọn hoặc nhóm tất cả Document có cùng key.
    - out xác định vị trí của kết quả truy vấn Map-Reduce.
    - query xác định tiêu chuẩn chọn tùy ý để lựa chọn các Document.
    - sort xác định tiêu chuẩn sắp xếp tùy ý.
    - limit xác định số lượng Document tối đa tùy ý để được trả về.

  - ex:
  ![ex](/images/1.jpg)
