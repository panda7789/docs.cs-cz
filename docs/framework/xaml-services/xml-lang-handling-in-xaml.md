---
title: Práce s atributem xml:lang v jazyce XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
ms.openlocfilehash: 98bfabba96e5805b96c63eb02233b15eae233cc0
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740565"
---
# <a name="xmllang-handling-in-xaml"></a>Práce s atributem xml:lang v jazyce XAML
Atribut `xml:lang` je atribut definovaný v jazyce XML, který deklaruje informace o jazyku a jazykové verzi elementu v jazyce XML. Stejný význam atributu v jazyce XAML přetrvává; platí však některé další požadavky.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<object xml:lang="rfc3066lang" />  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|*rfc3066lang*|Řetězec, který je odvozen z standardu [RFC 3066](https://go.microsoft.com/fwlink/?LinkId=132454) a označuje jazyk nebo jazykovou oblast. Pokud se jedná o druhý, jazyk a oblast jsou oddělené jedním spojovníkem. Další informace o hodnotách a formátu najdete v tématu <xref:System.Windows.Markup.XmlLanguage>.|  
  
## <a name="remarks"></a>Poznámky  
 Definice atributu `xml:lang` v [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] je odvozena z `xml:lang` definovaná jako "speciální atribut" konsorcium World Wide Web (W3C) pro XML. Informace o jazyku a jazykové verzi jsou potenciálně zpracovávány různými způsoby podle prvků v závislosti na jejich implementacích. Neexistuje však žádný výchozí [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] zpracování atributu `xml:lang`.  
  
 Výchozí hodnota atributu `xml:lang` je prázdný řetězec na úrovni atributu.  
  
 Vliv atributů `xml:lang` a hodnota atributu jsou obecně perpetuated na podřízené prvky, pokud jsou interpretovány systémy, které pracují s hodnotami `xml:lang`.  
  
 Při interpretaci autory XAML .NET Frameworkch služeb XAML může `xml:lang` hodnotu vytvořit <xref:System.Windows.Markup.XmlLanguage> nebo <xref:System.Globalization.CultureInfo> objekty v reprezentaci podkladových objektů; Toto chování je však závislé na tom, zda je hodnota zadaná pro `xml:lang` platnou konstrukcí pro tyto třídy.  
  
 Rozhraní můžou vytvořit přidružení mezi vlastnostmi definovanými rozhraním a významem `xml:lang` v XML, a to použitím <xref:System.Windows.Markup.XmlLangPropertyAttribute> na vlastnost.  
  
## <a name="wpf-usage-nodes"></a>Uzly použití WPF  
 Pro prvky, které jsou odvozeny třídy <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>, lze namísto atributu `xml:lang` použít ekvivalentní vlastnost Dependency <xref:System.Windows.FrameworkElement.Language%2A>. Ve výchozím nastavení vlastnost <xref:System.Windows.FrameworkElement.Language%2A> používá "en-US", pokud není jinak nastavena, buď prostřednictvím vlastnosti, nebo prostřednictvím zpracování atributu `xml:lang`.  
  
## <a name="see-also"></a>Viz také:

- [Globalizace pro WPF](../wpf/advanced/globalization-for-wpf.md)
