# how-to-bind-the-SelectedItem-property-of-wpf-tree-grid-in-mvvm

This example illustrates to bind the `SelectedItem` property from ViewModel to the [SelectedItem](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Grid.SfGridBase.html#Syncfusion_UI_Xaml_Grid_SfGridBase_SelectedItem) Property of [WPF TreeGrid](https://www.syncfusion.com/wpf-controls/treegrid) and [UWP TreeGrid](https://www.syncfusion.com/uwp-ui-controls/treegrid).

You can bind the `SelectedItem` property directly to `TreeGrid` by setting the [SfTreeGrid.SelectedItem](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Grid.SfGridBase.html#Syncfusion_UI_Xaml_Grid_SfGridBase_SelectedItem) property.

## XAML code:

``` xml
<syncfusion:SfTreeGrid Name="treeGrid" 
                               Grid.Row="1" 
                               ChildPropertyName="ReportsTo"  
                               AutoExpandMode="AllNodesExpanded"
                               ShowRowHeader="True" 
                               SelectedItem="{Binding SelectedItem, Mode=TwoWay, UpdateSourceTrigger=PropertyChanged}"
                               AutoGenerateColumns="False"
                               ItemsSource="{Binding Employees}"
                               ParentPropertyName="ID"
                               SelfRelationRootValue="-1"/>

```

## C# code:

``` C#
public class ViewModel: NotificationObject
{
    private object selectedItem;
    public object SelectedItem
    {
        get
        {
           return selectedItem;
        }
        set
        {
           selectedItem = value;
           RaisePropertyChanged("SelectedItem");
        }
    }
}
```