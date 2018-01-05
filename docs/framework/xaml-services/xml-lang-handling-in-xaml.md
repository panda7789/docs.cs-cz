---
title: "Práce s atributem xml:lang v jazyce XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
caps.latest.revision: "16"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3dad1600d93f53198d7ca7842148612b7755fc10
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="xmllang-handling-in-xaml"></a>Práce s atributem xml:lang v jazyce XAML
`xml:lang` Atribut je [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)]-definovaný atribut, který deklaruje informace o jazyce a jazykové verzi pro element v kódu XML. Tento stejný význam atributu přetrvává v jazyce XAML; ale některé další aspekty platí.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<object xml:lang="rfc3066lang" />  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|*rfc3066lang*|Řetězec, který je odvozený od [RFC 3066](http://go.microsoft.com/fwlink/?LinkId=132454) standardní a identifikuje jazyk nebo jazyka oblasti. Pokud je k tomu, jazyk a oblasti jsou oddělena pomlčkou jeden. V tématu <xref:System.Windows.Markup.XmlLanguage> Další informace o hodnoty a formát.|  
  
## <a name="remarks"></a>Poznámky  
 Definice pro `xml:lang` atribut [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] je odvozený od `xml:lang` podle definice jako "speciální atribut" [!INCLUDE[TLA#tla_w3c](../../../includes/tlasharptla-w3c-md.md)] pro [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)]. Informace o jazyce a jazykové verzi potenciálně zpracovává různými způsoby prvky, v závislosti na jejich implementace; neexistuje však žádný výchozí [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] zpracování `xml:lang` atribut.  
  
 Výchozí hodnota `xml:lang` atribut je prázdný řetězec na úrovni atribut.  
  
 `xml:lang` Atribut dopady a hodnota atributu jsou obecně perpetuated pro podřízené elementy, když interpretovat systémy, které fungují v `xml:lang` hodnoty.  
  
 Když interpretovat XAML zapisovače služby rozhraní .NET Framework XAML Services `xml:lang` můžete vytvořit hodnotu <xref:System.Windows.Markup.XmlLanguage> nebo <xref:System.Globalization.CultureInfo> objekty v základní objektu reprezentace; ale, že chování závisí na tom, zda zadaná hodnota parametru `xml:lang`je platná konstrukce pro tyto třídy.  
  
 Rozhraní můžete vytvořit přidružení mezi framework definované vlastnosti a význam `xml:lang` v kódu XML s použitím <xref:System.Windows.Markup.XmlLangPropertyAttribute> pro vlastnost.  
  
## <a name="wpf-usage-nodes"></a>Uzly využití grafického subsystému WPF  
 Pro prvky, které jsou odvozené třídy <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>, můžete ekvivalentní <xref:System.Windows.FrameworkElement.Language%2A> vlastnost závislosti místo `xml:lang` atribut. Ve výchozím nastavení <xref:System.Windows.FrameworkElement.Language%2A> vlastnost používá "en US", pokud není jinak nastavené, vlastnost prostřednictvím nebo zpracování `xml:lang` atribut.  
  
## <a name="see-also"></a>Viz také  
 [Globalizace pro WPF](../../../docs/framework/wpf/advanced/globalization-for-wpf.md)
