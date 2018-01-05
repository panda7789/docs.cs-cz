---
title: "Postupy: Připojení k XDocument, XElement nebo LINQ pro výsledky XML dotazu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to XDocument
- data binding [WPF], binding to XElement
ms.assetid: 6a629a49-fe1c-465d-b76a-3dcbf4307b64
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ceb6023157d487aebeff4fb5335b58c0958f2851
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results"></a>Postupy: Připojení k XDocument, XElement nebo LINQ pro výsledky XML dotazu
Tento příklad ukazuje, jak vytvořit vazbu dat XML do <xref:System.Windows.Controls.ItemsControl> pomocí <xref:System.Xml.Linq.XDocument>.  
  
## <a name="example"></a>Příklad  
 Následující kód XAML definuje <xref:System.Windows.Controls.ItemsControl> a obsahuje šablonu dat pro data typu `Planet` v `http://planetsNS` obor názvů XML. Datový typ XML, který bude zabírat oboru názvů musí zahrnovat oboru názvů do složených závorek a pokud se zobrazí, kde se může zobrazit rozšíření značek XAML, je třeba zadat jeden obor názvů s řídicí sekvence závorek. Tento kód se váže k dynamické vlastnosti, které odpovídají <xref:System.Xml.Linq.XContainer.Element%2A> a <xref:System.Xml.Linq.XElement.Attribute%2A> metody <xref:System.Xml.Linq.XElement> třídy. Dynamické vlastnosti povolit XAML pro vazbu k dynamické vlastnosti, které sdílejí názvy metod. Další informace najdete v tématu [technologie LINQ to XML dynamické vlastnosti](/visualstudio/designers/linq-to-xml-dynamic-properties). Všimněte si, jak výchozí deklaraci oboru názvů pro soubor XML nevztahuje na názvy atributů.  
  
 [!code-xaml[XLinqExample#StackPanelResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
[!code-xaml[XLinqExample#ItemsControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#itemscontrol)]  
  
 Následující volání kódu jazyka C# <xref:System.Xml.Linq.XDocument.Load%2A> a nastaví kontext zásobníku panel data na všechny dílčí prvky elementu s názvem `SolarSystemPlanets` v `http://planetsNS` obor názvů XML.  
  
 [!code-csharp[XLinqExample#LoadDCFromFile](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromfile)]
 [!code-vb[XLinqExample#LoadDCFromFile](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromfile)]  
  
 XML data mohou být uloženy ve formě XAML prostředků pomocí <xref:System.Windows.Data.ObjectDataProvider>. Úplný příklad najdete v tématu [L2DBForm.xaml zdrojový kód](http://msdn.microsoft.com/library/624e96d4-6d27-4195-8ac2-2f3835f6c57e). Následující příklad ukazuje, jak kód můžete nastavit kontext dat na prostředek objektu.  
  
 [!code-csharp[XLinqExample#LoadDCFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromxaml)]
 [!code-vb[XLinqExample#LoadDCFromXAML](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromxaml)]  
  
 Dynamické vlastnosti, které jsou mapovány na <xref:System.Xml.Linq.XContainer.Element%2A> a <xref:System.Xml.Linq.XElement.Attribute%2A> poskytují flexibilitu v rámci XAML. Váš kód můžete také vytvořit vazbu k výsledky LINQ pro dotaz XML. Tento příklad vytvoří vazbu s výsledky dotazů, které jsou seřazené podle hodnotu elementu.  
  
 [!code-csharp[XLinqExample#BindToResults](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#bindtoresults)]
 [!code-vb[XLinqExample#BindToResults](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#bindtoresults)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled zdrojů vazby](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [Přehled datové vazby WPF s LINQ to XML](/visualstudio/designers/wpf-data-binding-with-linq-to-xml-overview)  
 [Příklad datové vazby WPF pomocí LINQ to XML](/visualstudio/designers/wpf-data-binding-using-linq-to-xml-example)  
 [Dynamické vlastnosti LINQ to XML](/visualstudio/designers/linq-to-xml-dynamic-properties)
