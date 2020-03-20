---
title: Kód na pozadí a XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], code-behind
- code-behind files [WPF], XAML
ms.assetid: 9df6d3c9-aed3-471c-af36-6859b19d999f
ms.openlocfilehash: 32283d5b81bf92999a97711ded13a8b533ae3028
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145342"
---
# <a name="code-behind-and-xaml-in-wpf"></a>Podkladový kód a kód XAML v subsystému WPF
<a name="introduction"></a>Kód na pozadí je termín používaný k popisu kódu, který je [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] spojen s objekty definované značkami, když je stránka zkompilován značky. Toto téma popisuje požadavky na kód na pozadí, stejně [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]jako alternativní mechanismus vřádkového kódu pro kód v aplikaci .  
  
 Toto téma obsahuje následující oddíly:  
  
- [Požadavky](#Prerequisites)  
  
- [Kód na pozadí a jazyk XAML](#codebehind_and_the_xaml_language)  
  
- [Kód na pozadí, obslužná rutina událostí a požadavky na částečnou třídu v WPF](#Code_behind__Event_Handler__and_Partial_Class)  
  
- [x:Kód](#x_Code)  
  
- [Omezení vřádících kódů](#Inline_Code_Limitations)  
  
<a name="Prerequisites"></a>
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že jste si přečetli [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md) a mají některé základní znalosti CLR a objektově orientované programování.  
  
<a name="codebehind_and_the_xaml_language"></a>
## <a name="code-behind-and-the-xaml-language"></a>Kód na pozadí a jazyk XAML  
 Jazyk XAML obsahuje funkce na úrovni jazyka, které umožňují přidružit soubory kódu k souborům značek na straně souboru značek. Jazyk XAML konkrétně definuje vlastnosti jazyka [x:Class Directive](../../../desktop-wpf/xaml-services/xclass-directive.md), [x:Subclass Directive](../../../desktop-wpf/xaml-services/xsubclass-directive.md)a [x:ClassModifier Directive](../../../desktop-wpf/xaml-services/xclassmodifier-directive.md). Přesně tak, jak by měl být vytvořen kód a jak integrovat značky a kód, není součástí toho, co určuje jazyk XAML. Je ponecháno na architektury, jako je například WPF určit, jak integrovat kód, jak používat XAML v aplikacích a programovacích modelů a sestavení akce nebo jiné podpory, které to vše vyžaduje.  
  
<a name="Code_behind__Event_Handler__and_Partial_Class"></a>
## <a name="code-behind-event-handler-and-partial-class-requirements-in-wpf"></a>Kód na pozadí, obslužná rutina událostí a požadavky na částečnou třídu v WPF  
  
- Částečná třída musí být odvozena od typu, který podporuje kořenový prvek.  
  
- Všimněte si, že v rámci výchozí chování akce sestavení kompilace značky můžete ponechat odvození prázdné v definici částečné třídy na straně kód na pozadí. Zkompilovaný výsledek bude předpokládat, že typ zálohování kořenového adresáře stránky bude základem pro částečnou třídu, i když není zadán. Spoléhání se na toto chování však není osvědčeným postupem.  
  
- Obslužné rutiny událostí, které napíšete v kódu na pozadí, musí být metodami instance a nemohou být statickými metodami. Tyto metody musí být definovány částečnou třídou `x:Class`v oboru názvů CLR identifikovaném . Název obslužné rutiny události [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nelze kvalifikovat tak, aby dal procesoru pokyn, aby vyhledal obslužnou rutinu události pro zapojení události v jiném oboru třídy.  
  
- Obslužná rutina musí odpovídat delegátovi pro příslušnou událost v systému typu zálohování.  
  
- Pro jazyk Jazyka Microsoft Visual Basic konkrétně můžete `Handles` použít klíčové slovo specifické pro jazyk k přidružení obslužných rutin [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]s instancemi a událostmi v deklaraci obslužné rutiny, namísto připojení obslužných rutin s atributy v aplikaci . Tato technika však má určitá `Handles` omezení, protože klíčové slovo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nemůže podporovat všechny specifické funkce systému událostí, jako jsou například některé směrované scénáře událostí nebo připojené události. Podrobnosti naleznete v [tématu Visual Basic a WPF Event Handling](visual-basic-and-wpf-event-handling.md).  
  
<a name="x_Code"></a>
## <a name="xcode"></a>x:Kód  
 [x:Code](../../../desktop-wpf/xaml-services/xcode-intrinsic-xaml-type.md) je prvek směrnice [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]definovaný v . Prvek `x:Code` směrnice může obsahovat vřádkový programovací kód. Kód, který je definován v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] řádku můžete komunikovat s na stejné stránce. Následující příklad ilustruje vposlední řádek kódu Jazyka C#. Všimněte si, že `x:Code` kód je uvnitř prvku a `<CDATA[`že kód musí být obklopen ... `]]>` chcete-li uniknout obsah pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] XML, tak, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aby procesor (interpretace schématu nebo schématu) [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] se nepokusí interpretovat obsah doslova jako XML.  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithInlineCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page4.xaml#buttonwithinlinecode)]  
  
<a name="Inline_Code_Limitations"></a>
## <a name="inline-code-limitations"></a>Omezení vřádících kódů  
 Měli byste zvážit, zda se vyhnout nebo omezit použití vložkového kódu. Pokud jde o architekturu a filozofii kódování, udržování oddělení mezi značky a kód-behind udržuje návrháře a vývojáře role mnohem zřetelnější. Na techničtější úrovni může být kód, který píšete pro vložkový [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kód, nepříjemný, protože do generované částečné třídy vždy píšete a můžete použít pouze výchozí mapování oboru názvů XML. Vzhledem k `using` tomu, že nelze přidat příkazy, je nutné plně kvalifikovat mnoho volání rozhraní API, které provedete. Výchozí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mapování zahrnují většinu, ale ne všechny obory [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] názvů CLR, které jsou přítomny v sestaveních; budete muset plně kvalifikovat volání typů a členů obsažených v jiných oborech názvů CLR. Také nelze definovat nic nad rámec částečné třídy v včleněném kódu a všechny entity uživatelského kódu, na které odkazujete, musí existovat jako člen nebo proměnná v rámci generované částečné třídy. Další programovací funkce specifické pro `#ifdef` jazyk, například makra nebo globální proměnné nebo proměnné sestavení, také nejsou k dispozici. Další informace naleznete [v tématu x:Code Intrinsic XAML Type](../../../desktop-wpf/xaml-services/xcode-intrinsic-xaml-type.md).  
  
## <a name="see-also"></a>Viz také

- [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [x:Code – vnitřní typ jazyka XAML](../../../desktop-wpf/xaml-services/xcode-intrinsic-xaml-type.md)
- [Sestavení aplikace WPF](../app-development/building-a-wpf-application-wpf.md)
- [Podrobná syntaxe XAML](xaml-syntax-in-detail.md)
