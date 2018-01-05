---
title: "Jazykové funkce jazyka XAML 2009"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML 2009 [XAML Services]
- XAML [XAML Services], XAML 2009
ms.assetid: f6bb18d8-c86a-4549-8862-323e6b32a8dd
caps.latest.revision: "11"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 447ba37330e8027d86fd24239a8aca2461dce8d0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="xaml-2009-language-features"></a>Jazykové funkce jazyka XAML 2009
XAML 2009 je sdružená termín pro nové funkce jazyka XAML, které rozšiřují existující specifikace jazyka XAML. XAML 2009 zavádí několik nových direktivách a konstrukce. Patří mezi ně[x: Arguments – direktiva](../../../docs/framework/xaml-services/x-arguments-directive.md); [x: factorymethod – direktiva](../../../docs/framework/xaml-services/x-factorymethod-directive.md); [x: Reference – rozšíření značek](../../../docs/framework/xaml-services/x-reference-markup-extension.md); [x: TypeArguments – direktiva ](../../../docs/framework/xaml-services/x-typearguments-directive.md); a vestavěné typy pro běžné primitiv jazyka (například `x:Char`).  
  
<a name="xaml_2009_support_in_wpf_and_visual_studio"></a>   
## <a name="xaml-2009-support-in-wpf-and-visual-studio"></a>Podpora jazyka XAML 2009 v WPF a Visual Studio  
 V grafickém subsystému WPF můžete použít funkce jazyka XAML 2009, ale jenom pro jazyk XAML, který není WPF zkompilovat kód. Zkompilovaný kód XAML a BAML formu XAML aktuálně nepodporují klíčová slova jazyka XAML 2009 a funkce.  
  
 Nezapomeňte, že existující techniky pro načítání přijít XAML v grafickém subsystému WPF také mít možné zabezpečení a přístup omezení pro typy CLR a systém typů více omezující než zkompilovat kód XAML. Další informace najdete v tématu [zabezpečení (WPF)](../../../docs/framework/wpf/security-wpf.md) nebo [strategie zabezpečení WPF - platformy zabezpečení](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md).  
  
 Také zavádí další funkce, upravte předchozí 2006 XAML XAML 2009 konstrukce nebo který měnit základní značek formuláře.  
  
### <a name="xkey-as-an-object-element"></a>x: Key jako Element objektu  
 Může podporovat XAML 2009 `x:Key` jako objekt (na vlastnost element, který má hodnotu elementu objektu); však XAML 2006 podporuje jenom `x:Key` jako atribut. Najdete v části "XAML 2009" [x: Key – direktiva](../../../docs/framework/xaml-services/x-key-directive.md).  
  
### <a name="xmlns-on-property-elements"></a>atribut xmlns u vlastností elementů  
 XAML 2009 může podporovat definice oboru názvů (xmlns) XAML na elementy vlastnost; XAML 2006 však podporuje pouze xmlns definice na elementy objektu.  
  
### <a name="event-attributes"></a>Atributy událostí  
 Pro atributy, které jsou zajišťované události XAML 2006 předpokládá, že kompilace kódu se tak zapojí a odesílá události, které kompilace kódu. XAML 2009 podporuje značku formuláře, který vypadá takto: rozšíření značek, které odkládat údaje spojení události do doby běhu analýzy a načítání XAML. Však aplikace WPF a scénáře XAML pro uživatelské rozhraní WPF obecně nepoužívejte tuto funkci. WPF a jeho implementace XAML 2006 používá kombinaci spojení obslužné rutiny události pro směrované události definované na <xref:System.Windows.UIElement> úroveň a jeho značek kompilátoru krok pro většinu jeho atribut zpracování událostí. Kompilátor značek také upraví žádné atributy událostí najít v jazyce XAML, kde akce sestavení deklarovat, že se používá kompilátoru značek.  
  
## <a name="see-also"></a>Viz také  
 [Přehled XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
