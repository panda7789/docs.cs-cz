---
title: Podkladový kód a kód XAML v subsystému WPF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- XAML [WPF], code-behind
- code-behind files [WPF], XAML
ms.assetid: 9df6d3c9-aed3-471c-af36-6859b19d999f
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9c28a501996e4f2cc25e9e280b2f63e1c0c67051
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="code-behind-and-xaml-in-wpf"></a>Podkladový kód a kód XAML v subsystému WPF
<a name="introduction"></a> Kódu je termín, který používá k popisu kód, který je spojen s objekty definovanými značkami při [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránka je zkompilovaný kód. Toto téma popisuje požadavky pro kódu i mechanismus alternativní vloženého kódu pro kód ve [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Toto téma obsahuje následující oddíly:  
  
-   [Požadavky](#Prerequisites)  
  
-   [Kódu a jazyk XAML](#codebehind_and_the_xaml_language)  
  
-   [Kódu, obslužné rutiny události a požadavky na třídu v grafickém subsystému WPF](#Code_behind__Event_Handler__and_Partial_Class)  
  
-   [x: Code](#x_Code)  
  
-   [Omezení vloženého kódu](#Inline_Code_Limitations)  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že jste četli [přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) a mají některé základní znalosti o [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] a objektově orientované programování.  
  
<a name="codebehind_and_the_xaml_language"></a>   
## <a name="code-behind-and-the-xaml-language"></a>Kódu a jazyk XAML  
 Jazyk XAML zahrnuje úroveň jazyka funkce, které umožňují soubory kódu přidružit souborech značek ze strany souboru značek. Konkrétně jazyk XAML definuje funkce jazyka [x: Class – direktiva](../../../../docs/framework/xaml-services/x-class-directive.md), [x: Subclass – direktiva](../../../../docs/framework/xaml-services/x-subclass-directive.md), a [x: ClassModifier – direktiva](../../../../docs/framework/xaml-services/x-classmodifier-directive.md). Přesně jak by měla být vytvořena kód a jak integrovat značek a kódu, není součástí co určuje jazyk XAML. Je ponechán až architektury, jako je například WPF určit, jak integrovat kód, jak pokud chcete používat XAML v aplikaci a programovací modely a sestavení akce nebo jiné podporovat, to vše vyžaduje.  
  
<a name="Code_behind__Event_Handler__and_Partial_Class"></a>   
## <a name="code-behind-event-handler-and-partial-class-requirements-in-wpf"></a>Kódu, obslužné rutiny události a požadavky na třídu v grafickém subsystému WPF  
  
-   Částečné třídy musí být odvozeny od typu, který zálohuje kořenový element.  
  
-   Všimněte si, že v rámci výchozího chování akce sestavení kompilace kódu, můžete nechat odvození prázdné v definici částečné třídy na straně kódu. Kompilované výsledek bude předpokládají základní typ stránky kořenové jako základ pro třídu, i když není zadaný. Spoléhat na toto chování je však není osvědčený postup.  
  
-   Obslužné rutiny událostí, které můžete psát v kódu musí být instanci metody a nemůže být statické metody. Tyto metody musí být definované třídu v rámci oboru názvů CLR identifikovaný `x:Class`. Název obslužné rutiny události dáte pokyn, aby nelze kvalifikaci [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru a hledat obslužné rutiny události pro spojení události v oboru jinou třídu.  
  
-   Obslužná rutina se musí shodovat delegát pro odpovídající události v systému typ zálohování.  
  
-   Pro jazyk Microsoft Visual Basic konkrétně, můžete použít konkrétní jazyk `Handles` – klíčové slovo přidružit instancí a události v deklaraci obslužné rutiny, místo připojení obslužné rutiny s atributy v obslužné rutiny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Tento postup však má určitá omezení, protože `Handles` – klíčové slovo nemůže podporovat všechny konkrétní funkce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] událostí systému, například určité směrují scénáře událostí nebo přidružené události. Podrobnosti najdete v tématu [Visual Basic a zpracování události WPF](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).  
  
<a name="x_Code"></a>   
## <a name="xcode"></a>x: Code  
 [x: Code](../../../../docs/framework/xaml-services/x-code-intrinsic-xaml-type.md) element direktivy je definována v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. `x:Code` – Direktiva element může obsahovat vložené programového kódu. Kód, který je definována vložením mohou komunikovat s [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] na stejné stránce. Následující příklad ilustruje vloženého kódu C#. Všimněte si, že kód je uvnitř `x:Code` elementu a že kód musí být uzavřena do `<CDATA[`... `]]>` abyste se vyhnuli obsah pro [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]tak, aby [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru (interpretace buď [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schématu nebo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] schématu) nebude zkoušet interpretovat obsah oznámena jako [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)].  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithInlineCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page4.xaml#buttonwithinlinecode)]  
  
<a name="Inline_Code_Limitations"></a>   
## <a name="inline-code-limitations"></a>Omezení vloženého kódu  
 Měli byste zvážit vyloučení nebo omezení použití vloženého kódu. Z hlediska architektury a kódování filosofie zachování oddělení mezi značek a kódu udržuje role designer a vývojáře mnohem víc distinct. Na další technické úrovni, může být nevhodných k zápisu, kód, který zapisuje pro vloženého kódu vzhledem k tomu, že jsou vždy zápisu do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] vygeneruje třídu a můžou používat jenom výchozí mapování oboru názvů XML. Vzhledem k tomu, že nemůžete přidat `using` příkazy, které musí plnému určení řadu [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] volání, které provedete. Výchozí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mapování obsahovat nejvíce, ale ne všechny [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obory názvů, které jsou součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sestavení; bude mít k plnému určení volání typy a členy obsažené v jiných CLR oborech názvů. Můžete také nelze definovat nic nad třídu v vloženého kódu, a všechny entity kód uživatele, který odkazujete musí existovat jako proměnné v rámci generovaného třídu nebo člena. Další jazyk konkrétní programovací funkce, třeba makra nebo `#ifdef` proti globální proměnné nebo proměnné sestavení, nejsou k dispozici. Další informace najdete v tématu [x: Code vnitřní typ jazyka XAML](../../../../docs/framework/xaml-services/x-code-intrinsic-xaml-type.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [x:Code – vnitřní typ jazyka XAML](../../../../docs/framework/xaml-services/x-code-intrinsic-xaml-type.md)  
 [Sestavení aplikace WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [Podrobná syntaxe XAML](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)
