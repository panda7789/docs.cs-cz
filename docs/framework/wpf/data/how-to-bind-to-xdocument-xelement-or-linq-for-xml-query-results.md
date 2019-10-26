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
ms.openlocfilehash: 070f67f30613d4522a48e08fd1c208fbe5887525
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920113"
---
# <a name="how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results"></a>Postupy: Připojení k XDocument, XElement nebo LINQ pro výsledky XML dotazu

Tento příklad ukazuje, jak vytvořit vazby dat XML k <xref:System.Windows.Controls.ItemsControl> pomocí <xref:System.Xml.Linq.XDocument>.

## <a name="example"></a>Příklad

Následující kód XAML definuje <xref:System.Windows.Controls.ItemsControl> a obsahuje datovou šablonu pro data typu `Planet` v oboru názvů XML `http://planetsNS`. Datový typ XML, který zabírá obor názvů, musí obsahovat obor názvů v závorkách a pokud se zobrazí, kde se může zobrazit rozšíření značek XAML, musí předcházet tomuto oboru názvů řídicí sekvencí závorky. Tento kód se váže k dynamickým vlastnostem, které odpovídají <xref:System.Xml.Linq.XContainer.Element%2A> a <xref:System.Xml.Linq.XElement.Attribute%2A> metod třídy <xref:System.Xml.Linq.XElement>. Dynamické vlastnosti umožňují, aby se XAML váže k dynamickým vlastnostem, které sdílejí názvy metod. Další informace najdete v tématu [LINQ to XML dynamické vlastnosti](linq-to-xml-dynamic-properties.md). Všimněte si, jak výchozí deklaraci oboru názvů pro XML neplatí pro názvy atributů.

[!code-xaml[XLinqExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]
[!code-xaml[XLinqExample#ItemsControl](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#itemscontrol)]

Následující C# kód volá<xref:System.Xml.Linq.XDocument.Load%2A>a nastaví kontext dat panelu zásobníku na všechny dílčí prvky elementu s názvem`SolarSystemPlanets`v oboru názvů XML`http://planetsNS`.

[!code-csharp[XLinqExample#LoadDCFromFile](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromfile)]
[!code-vb[XLinqExample#LoadDCFromFile](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromfile)]

Data XML lze uložit jako prostředek XAML pomocí <xref:System.Windows.Data.ObjectDataProvider>. Úplný příklad naleznete v tématu [zdrojový kód zdrojový kód L2DBForm. XAML](l2dbform-xaml-source-code.md). Následující příklad ukazuje, jak kód může nastavit kontext dat na prostředek objektu.

[!code-csharp[XLinqExample#LoadDCFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromxaml)]
[!code-vb[XLinqExample#LoadDCFromXAML](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromxaml)]

Dynamické vlastnosti, které jsou mapovány na <xref:System.Xml.Linq.XContainer.Element%2A> a <xref:System.Xml.Linq.XElement.Attribute%2A> poskytují flexibilitu v jazyce XAML. Váš kód může také vytvořit vazby k výsledkům dotazu LINQ for XML. Tento příklad váže k výsledkům dotazu seřazenými podle hodnoty elementu.

[!code-csharp[XLinqExample#BindToResults](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#bindtoresults)]
[!code-vb[XLinqExample#BindToResults](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#bindtoresults)]

## <a name="see-also"></a>Viz také:

- [Přehled zdrojů vazby](binding-sources-overview.md)
- [Přehled datové vazby WPF s LINQ to XML](wpf-data-binding-with-linq-to-xml-overview.md)
- [Příklad datové vazby WPF pomocí LINQ to XML](linq-to-xml-data-binding-sample.md)
- [Dynamické vlastnosti LINQ to XML](linq-to-xml-dynamic-properties.md)
