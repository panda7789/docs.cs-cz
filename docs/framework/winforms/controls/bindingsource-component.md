---
title: BindingSource – komponenta
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], Windows Forms
- Windows Forms, data binding control
- BindingSource component [Windows Forms]
ms.assetid: 3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9
ms.openlocfilehash: 0d07dc0ddf5e80d51d1494ff3398eeab150c3f26
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="bindingsource-component"></a>BindingSource – komponenta
Zapouzdří zdroj dat pro vytvoření vazby na ovládací prvky.  
  
 <xref:System.Windows.Forms.BindingSource> Součást má dva účely. Nejprve poskytuje úroveň dereference při vytvoření vazby ovládacích prvků na formuláři na data. Toho dosahuje pomocí vytvoření vazby <xref:System.Windows.Forms.BindingSource> součásti pro zdroj dat a následným vytvoření vazby ovládacích prvků na formuláři na <xref:System.Windows.Forms.BindingSource> součásti. Všechny další interakce s daty, včetně navigace, řazení, filtrování a aktualizace, se provádí pomocí volání <xref:System.Windows.Forms.BindingSource> součásti.  
  
 Druhý, <xref:System.Windows.Forms.BindingSource> součást může fungovat jako zdroj dat silného typu. Přidání typu k <xref:System.Windows.Forms.BindingSource> součásti s <xref:System.Windows.Forms.BindingSource.Add%2A> metoda vytvoří seznam daného typu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled komponenty BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)  
 Představuje obecné koncepty <xref:System.Windows.Forms.BindingSource> komponenta, která umožňuje svázat zdroj dat k ovládacímu prvku.  
  
 [Postupy: Vytvoření vazby ovládacích prvků Windows Forms k hodnotám databáze DBNull](../../../../docs/framework/winforms/controls/how-to-bind-windows-forms-controls-to-dbnull-database-values.md)  
 Ukazuje, jak zpracovat <xref:System.DBNull> hodnotu ze zdroje dat pomocí <xref:System.Windows.Forms.BindingSource> součásti.  
  
 [Postupy: Řazení a filtrování dat ADO.NET pomocí komponenty Windows Forms BindingSource](../../../../docs/framework/winforms/controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)  
 Ukazuje, jak pomocí <xref:System.Windows.Forms.BindingSource> součást použít seřadí a filtrů zobrazená data.  
  
 [Postupy: Vytvoření vazby k webové službě pomocí Windows Forms BindingSource](../../../../docs/framework/winforms/controls/how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource.md)  
 Ukazuje, jak používat <xref:System.Windows.Forms.BindingSource> součásti pro připojení k webové službě.  
  
 [Postupy: Zpracování chyb a výjimek, k nimž došlo v souvislosti s datovou vazbou](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)  
 Ukazuje, jak pomocí <xref:System.Windows.Forms.BindingSource> součásti pro pohodlné zpracování chyb vzniklých v operaci vazby na data.  
  
 [Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)  
 Ukazuje, jak pomocí <xref:System.Windows.Forms.BindingSource> součásti pro vazbu na typ.  
  
 [Postupy: Vytvoření vazby ovládacího prvku Windows Forms k objektu factory](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-factory-object.md)  
 Ukazuje, jak pomocí <xref:System.Windows.Forms.BindingSource> součást vytvořit vazbu objekt factory nebo metoda.  
  
 [Postupy: Přizpůsobení přidávání položek pomocí Windows Forms BindingSource](../../../../docs/framework/winforms/controls/how-to-customize-item-addition-with-the-windows-forms-bindingsource.md)  
 Ukazuje, jak pomocí <xref:System.Windows.Forms.BindingSource> součást je přidejte do zdroje dat a vytvořit nové položky.  
  
 [Postupy: Vytváření oznámení o změnách pomocí metody BindingSource ResetItem](../../../../docs/framework/winforms/controls/how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)  
 Ukazuje, jak pomocí <xref:System.Windows.Forms.BindingSource> součást umožňuje aktivovat události upozornění na změnu pro oznámení o změně zdroje dat, které nepodporují.  
  
 [Postupy: Vytváření oznámení o změnách pomocí rozhraní BindingSource a INotifyPropertyChanged](../../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md)  
 Ukazuje, jak používat typ, který dědí z <xref:System.ComponentModel.INotifyPropertyChanged> s <xref:System.Windows.Forms.BindingSource> ovládacího prvku.  
  
 [Postupy: Uplatňování aktualizací zdroje dat v ovládacím prvku Windows Forms pomocí BindingSource](../../../../docs/framework/winforms/controls/reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)  
 Ukazuje, jak reagovat na změny v zdroje dat pomocí <xref:System.Windows.Forms.BindingSource> součásti.  
  
 [Postupy: Sdílení vázaných dat mezi formuláři pomocí komponenty BindingSource](../../../../docs/framework/winforms/controls/how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)  
 Ukazuje, jak používat <xref:System.Windows.Forms.BindingSource> k vytvoření vazby formuláře více stejný zdroj dat.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Windows.Forms.BindingSource>  
 Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.BindingSource> součásti.  
  
 <xref:System.Windows.Forms.BindingNavigator>  
 Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.BindingNavigator> ovládacího prvku.  
  
## <a name="related-sections"></a>Související oddíly  
 [Windows Forms – datová vazba](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 Obsahuje odkazy na témata s popisem architektuře vazby dat Windows Forms.  
  
 Viz také [vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).
