---
title: BindingSource – komponenta
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], Windows Forms
- Windows Forms, data binding control
- BindingSource component [Windows Forms]
ms.assetid: 3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9
ms.openlocfilehash: 54639edb512a8bc6c5909282d5e4c210439e2a6e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717593"
---
# <a name="bindingsource-component"></a>BindingSource – komponenta
Zapouzdřuje zdroj dat pro vytvoření vazby na ovládací prvky.  
  
 <xref:System.Windows.Forms.BindingSource> Komponenta má dva účely. Nejprve poskytuje úroveň dereference při vytvoření vazby ovládacích prvků ve formuláři na data. To lze provést pomocí vytvoření vazby <xref:System.Windows.Forms.BindingSource> zdroje dat a následným vytvoření vazby ovládacích prvků na formuláři pro komponentu <xref:System.Windows.Forms.BindingSource> komponenty. Všechny další interakce s daty, včetně navigace, řazení, filtrování a aktualizace, se provádí pomocí volání <xref:System.Windows.Forms.BindingSource> komponenty.  
  
 Druhý, <xref:System.Windows.Forms.BindingSource> komponenta může fungovat jako zdroj dat silného typu. Přidání typu <xref:System.Windows.Forms.BindingSource> komponentu s <xref:System.Windows.Forms.BindingSource.Add%2A> metoda vytvoří seznam daného typu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled komponenty BindingSource](bindingsource-component-overview.md)  
 Představuje obecné koncepty <xref:System.Windows.Forms.BindingSource> součásti, která umožňuje vytvoření vazby zdroje dat k ovládacímu prvku.  
  
 [Postupy: Vytvoření vazby ovládacích prvků Windows Forms k hodnotám databáze DBNull](how-to-bind-windows-forms-controls-to-dbnull-database-values.md)  
 Ukazuje, jak zpracovat <xref:System.DBNull> hodnoty ze zdroje dat s použitím <xref:System.Windows.Forms.BindingSource> komponenty.  
  
 [Postupy: Řazení a filtrování dat ADO.NET pomocí Windows Forms BindingSource – komponenta](sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)  
 Ukazuje použití <xref:System.Windows.Forms.BindingSource> seřadí součást, kterou použít a filtruje data zobrazená.  
  
 [Postupy: Připojení k webové službě pomocí Windows Forms BindingSource](how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource.md)  
 Ukazuje způsob použití <xref:System.Windows.Forms.BindingSource> součásti pro vytvoření vazby k webové službě.  
  
 [Postupy: Zpracování chyb a výjimek, ke kterým dochází s datovou vazbou](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)  
 Ukazuje použití <xref:System.Windows.Forms.BindingSource> komponenty pro pohodlné zpracování chyb, ke kterým dochází v datové vazbě operace.  
  
 [Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu](how-to-bind-a-windows-forms-control-to-a-type.md)  
 Ukazuje použití <xref:System.Windows.Forms.BindingSource> součásti pro vytvoření vazby k typu.  
  
 [Postupy: Vytvoření vazby ovládacího prvku Windows Forms k objektu Factory](how-to-bind-a-windows-forms-control-to-a-factory-object.md)  
 Ukazuje použití <xref:System.Windows.Forms.BindingSource> součásti pro vytvoření vazby na objekt pro vytváření objektu nebo metody.  
  
 [Postupy: Přizpůsobení přidávání položek pomocí Windows Forms BindingSource](how-to-customize-item-addition-with-the-windows-forms-bindingsource.md)  
 Ukazuje použití <xref:System.Windows.Forms.BindingSource> součásti pro vytvoření nové položky a přidat je do zdroje dat.  
  
 [Postupy: Vytváření oznámení o změnách pomocí metody BindingSource Resetitem](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)  
 Ukazuje použití <xref:System.Windows.Forms.BindingSource> součást, kterou vyvolávají události oznamování změn pro oznámení o změně zdroje dat, které nepodporují.  
  
 [Postupy: Vytváření oznámení o změnách pomocí BindingSource a INotifyPropertyChanged – rozhraní](raise-change-notifications--bindingsource.md)  
 Ukazuje, jak použít typ, který dědí z <xref:System.ComponentModel.INotifyPropertyChanged> s <xref:System.Windows.Forms.BindingSource> ovládacího prvku.  
  
 [Postupy: Uplatňování aktualizací zdroje dat v ovládacím prvku Windows Forms pomocí BindingSource](reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)  
 Ukazuje, jak reagovat na změny ve zdroji dat pomocí <xref:System.Windows.Forms.BindingSource> komponenty.  
  
 [Postupy: Sdílení vázaných dat mezi formuláři pomocí komponenty BindingSource](how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)  
 Ukazuje způsob použití <xref:System.Windows.Forms.BindingSource> svázat více formulářů do stejného datového zdroje.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Windows.Forms.BindingSource>  
 Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.BindingSource> komponenty.  
  
 <xref:System.Windows.Forms.BindingNavigator>  
 Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.BindingNavigator> ovládacího prvku.  
  
## <a name="related-sections"></a>Související oddíly  
 [Windows Forms – datová vazba](../windows-forms-data-binding.md)  
 Obsahuje odkazy na témata popisující architektura vazby dat formuláře Windows.  
  
 Viz také [vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).
