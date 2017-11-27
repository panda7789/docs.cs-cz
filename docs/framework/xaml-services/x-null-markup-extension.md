---
title: "x:Null – rozšíření značek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- NullExtension
- x:NullExtension
- x:Null
- Null
- xNull
helpviewer_keywords:
- Null markup extension in XAML [XAML Services]
- x:Null markup extension [XAML Services]
- XAML [XAML Services], x:Null markup extension
ms.assetid: 2e3ccc21-4996-481d-91b5-3910d8b3bfa3
caps.latest.revision: "20"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: a60d74bdf3343d02eaf912ac7700f36a649f659c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="xnull-markup-extension"></a>x:Null – rozšíření značek
Určuje `null` jako hodnotu pro člena XAML.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a>Poznámky  
 Klíčové slovo pro odkaz s hodnotou null v [!INCLUDE[TLA#tla_cshrp](../../../includes/tlasharptla-cshrp-md.md)] a [!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)] má hodnotu null. [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)] – Klíčové slovo pro odkaz s hodnotou null je `Nothing`, ale vždy používají `{x:Null}` jako bez ohledu na to XAML využití jazyk kódu, který přidružíte XAML.  
  
 `x:Null` – Rozšíření značek nemá žádné nastavit vlastnosti.  
  
 Použití null je často přidružen expozici člen XAML CLR <xref:System.Nullable%601> hodnotu.  
  
 `x:Null` – Rozšíření značek, například všechny XAML – rozšíření značek, používá složené závorky (`{,}`) pro zpracování hodnot atributu být jiné než literály nebo obslužná rutina události odkazy uvozovací znaky. Atribut syntaxe je syntaxe nejčastěji používá u tohoto rozšíření značek. Syntaxe elementu objektu `<x:Null />` je technicky možné, ale se používá zřídka, protože `x:Null` – rozšíření značek neobsahuje poziční parametry ani argumenty konstrukce.  
  
 Informace o rozšíření značek najdete v tématu [rozšíření značek a WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 V rozhraní .NET Framework XAML Services je definované zpracování pro toto rozšíření značek <xref:System.Windows.Markup.NullExtension> třídy.  
  
## <a name="wpf-usage-notes"></a>Poznámky pro použití WPF  
 Všimněte si, že `null` není nutně počáteční nenastavenou hodnotu pro vlastnost závislosti typu odkazu. Počáteční výchozí hodnota pro každou vlastnost závislosti se může lišit a může být založené na metadata specifická pro vlastnost. Mnoho vlastností závislostí nepřijímají `null` jako hodnotu, buď prostřednictvím kód z důvodu jejich implementace zpětného volání pro ověření. Další informace o vlastnostech závislostí v tématu [přehled vlastností závislostí](../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.DependencyProperty.UnsetValue>  
 [Přehled XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Rozšíření značek a WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
