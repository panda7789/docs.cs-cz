---
title: Práce s atributem xml:lang v jazyce XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
ms.openlocfilehash: 6495e980beea8731c47a774589919f160b4551ca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053597"
---
# <a name="xmllang-handling-in-xaml"></a>Práce s atributem xml:lang v jazyce XAML
`xml:lang` Atribut je [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)]-definovaný atribut, který deklaruje informace o jazyk a jazykovou verzi pro element v XML. Tento stejný význam atributu přetrvává v XAML; však použít několik dalších důležitých informací.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<object xml:lang="rfc3066lang" />  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|*rfc3066lang*|Řetězec, který je odvozen z [RFC 3066](https://go.microsoft.com/fwlink/?LinkId=132454) standardní a identifikuje jazyka nebo jazyka oblasti. Pokud je to ten, jazyka a oblasti jsou oddělené pomlčkou jeden. Zobrazit <xref:System.Windows.Markup.XmlLanguage> Další informace o hodnotách a formát.|  
  
## <a name="remarks"></a>Poznámky  
 Definice `xml:lang` atribut [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] je odvozen z `xml:lang` definované jako "speciální atribut" [!INCLUDE[TLA#tla_w3c](../../../includes/tlasharptla-w3c-md.md)] pro [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)]. Informace o jazyk a jazykovou verzi potenciálně zpracovává různými způsoby prvků, v závislosti na jejich implementace; neexistuje však žádný výchozí [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] zpracování `xml:lang` atribut.  
  
 Výchozí hodnota `xml:lang` atributu je prázdný řetězec na úrovni atribut.  
  
 `xml:lang` Efekty atribut a hodnota atributu jsou obecně perpetuated pro podřízené prvky, když jsou interpretovány systémy, které působí na `xml:lang` hodnoty.  
  
 Když interpretovat XAML zapisovače rozhraní .NET Framework XAML Services `xml:lang` může vytvořit hodnotu <xref:System.Windows.Markup.XmlLanguage> nebo <xref:System.Globalization.CultureInfo> reprezentace objektů v základním objektu, ale toto chování závisí na tom, zda hodnota zadaná pro omezení `xml:lang`je platná konstrukce pro tyto třídy.  
  
 Rozhraní může vytvořit přidružení mezi vlastnosti definované v rámci rozhraní a význam `xml:lang` ve formátu XML použitím <xref:System.Windows.Markup.XmlLangPropertyAttribute> na vlastnost.  
  
## <a name="wpf-usage-nodes"></a>Využití uzlů WPF  
 Pro prvky, které jsou odvozené třídy <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>, můžete ekvivalentní <xref:System.Windows.FrameworkElement.Language%2A> vlastnost závislosti místo `xml:lang` atribut. Ve výchozím nastavení <xref:System.Windows.FrameworkElement.Language%2A> vlastnost používá "en US", pokud není jinak nastavena, prostřednictvím vlastnosti nebo prostřednictvím zpracování `xml:lang` atribut.  
  
## <a name="see-also"></a>Viz také:

- [Globalizace pro WPF](../wpf/advanced/globalization-for-wpf.md)
