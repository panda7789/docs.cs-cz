---
title: 'Postupy: Připojení k XDocument, XElement nebo LINQ pro výsledky XML dotazu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to XDocument
- data binding [WPF], binding to XElement
ms.assetid: 6a629a49-fe1c-465d-b76a-3dcbf4307b64
ms.openlocfilehash: 0d68eb40b60481709ff2852a643908025e2e43ed
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54512330"
---
# <a name="how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results"></a>Postupy: Připojení k XDocument, XElement nebo LINQ pro výsledky XML dotazu
Tento příklad ukazuje, jak vytvořit vazbu dat XML do <xref:System.Windows.Controls.ItemsControl> pomocí <xref:System.Xml.Linq.XDocument>.  
  
## <a name="example"></a>Příklad  
 Definuje následující kód XAML <xref:System.Windows.Controls.ItemsControl> a obsahuje šablonu dat pro datový typ `Planet` v `http://planetsNS` oboru názvů XML. Datový typ XML, který zabírá oboru názvů musí obsahovat obor názvů ve složených závorkách, a pokud se zobrazí, kde se může zobrazit rozšíření značek XAML, musí být obor názvů se řídicí sekvence složenou závorku. Tento kód váže k dynamické vlastnosti, které odpovídají <xref:System.Xml.Linq.XContainer.Element%2A> a <xref:System.Xml.Linq.XElement.Attribute%2A> metody <xref:System.Xml.Linq.XElement> třídy. Dynamické vlastnosti umožňují XAML vytvořit vazbu na dynamické vlastnosti, které sdílejí názvy metod. Další informace najdete v tématu [XML dynamické vlastnosti LINQ to](/visualstudio/designers/linq-to-xml-dynamic-properties). Všimněte si, jak výchozí deklaraci oboru názvů pro XML se nevztahují na názvy atributů.  
  
 [!code-xaml[XLinqExample#StackPanelResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
[!code-xaml[XLinqExample#ItemsControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#itemscontrol)]  
  
 Následující volání kódu C# <xref:System.Xml.Linq.XDocument.Load%2A> a nastavuje kontext dat panelu zásobníku pro všechny dílčí prvky prvku s názvem `SolarSystemPlanets` v `http://planetsNS` oboru názvů XML.  
  
 [!code-csharp[XLinqExample#LoadDCFromFile](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromfile)]
 [!code-vb[XLinqExample#LoadDCFromFile](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromfile)]  
  
 XML data mohou být uložena jako prostředků XAML pomocí <xref:System.Windows.Data.ObjectDataProvider>. Kompletní příklad naleznete v tématu [zdrojový kód L2DBForm.xaml](https://msdn.microsoft.com/library/624e96d4-6d27-4195-8ac2-2f3835f6c57e). Následující příklad ukazuje, jak kód můžete nastavit kontext dat do objektu prostředku.  
  
 [!code-csharp[XLinqExample#LoadDCFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromxaml)]
 [!code-vb[XLinqExample#LoadDCFromXAML](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromxaml)]  
  
 Dynamické vlastnosti, které mapují na <xref:System.Xml.Linq.XContainer.Element%2A> a <xref:System.Xml.Linq.XElement.Attribute%2A> poskytují flexibilitu v rámci XAML. Kód můžete také navázat pro výsledky XML dotazu LINQ. Tento příklad vytvoří vazbu na výsledky dotazu seřazené podle hodnotu elementu.  
  
 [!code-csharp[XLinqExample#BindToResults](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#bindtoresults)]
 [!code-vb[XLinqExample#BindToResults](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#bindtoresults)]  
  
## <a name="see-also"></a>Viz také:
- [Přehled zdrojů vazby](../../../../docs/framework/wpf/data/binding-sources-overview.md)
- [Přehled datové vazby WPF s LINQ to XML](/visualstudio/designers/wpf-data-binding-with-linq-to-xml-overview)
- [Příklad datové vazby WPF pomocí LINQ to XML](/visualstudio/designers/wpf-data-binding-using-linq-to-xml-example)
- [Dynamické vlastnosti LINQ to XML](/visualstudio/designers/linq-to-xml-dynamic-properties)
