# How to get cell details when right-clicking a cell in Flutter DataGrid (SfDataGrid)?.

In this article, we will show you how to get cell details when right-clicking a cell in [Flutter DataGrid](https://www.syncfusion.com/flutter-widgets/flutter-datagrid).

Initialize the [SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html) widget with all required properties. Details about the right-clicked cell, such as rowColumnIndex, column, localPosition, and globalPosition, can be accessed through [DataGridCellTapDetails](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridCellTapDetails-class.html), which is passed as a parameter in the [onCellSecondaryTap](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid/onCellSecondaryTap.html) callback. Furthermore, you can retrieve the value of the tapped cell from the [effectiveRows](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/DataGridSource/effectiveRows.html) collection using the [RowColumnIndex.rowIndex](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/RowColumnIndex/rowIndex.html) property.

```dart
onCellSecondaryTap: (details) {
  showDialog(
    context: context,
    builder: (BuildContext context) {
      return AlertDialog(
        title: const Text('Tapped Cell Information'),
        content: SingleChildScrollView(
          child: ListBody(
            children: <Widget>[
              Text(
                'Column Index: ${details.rowColumnIndex.columnIndex}\n'
                'Row Index: ${details.rowColumnIndex.rowIndex}\n'
                'Column Name: ${details.column.columnName}',
              ),
              const SizedBox(height: 8),
              // Fetch details of the tapped cell value, excluding header cells.
              if (details.rowColumnIndex.rowIndex != 0)
                Text(
                  'Cell Value: ${employeeDataSource.effectiveRows[details.rowColumnIndex.rowIndex - 1].getCells()[details.rowColumnIndex.columnIndex].value}',
                ),
            ],
          ),
        ),
        actions: <Widget>[
          TextButton(
            child: const Text('OK'),
            onPressed: () {
              Navigator.of(context).pop();
            },
          ),
        ],
      );
    },
  );
},
```

You can download this example on [GitHub](https://github.com/SyncfusionExamples/How-to-get-cell-details-when-right-clicking-a-cell-in-Flutter-DataGrid).