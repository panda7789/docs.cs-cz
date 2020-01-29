---
title: Kód na pozadí a XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], code-behind
- code-behind files [WPF], XAML
ms.assetid: 9df6d3c9-aed3-471c-af36-6859b19d999f
ms.openlocfilehash: 212a37fb7fbcb7e66a669d96671333be793956df
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738102"
---
# <a name="code-behind-and-xaml-in-wpf"></a>Podkladový kód a kód XAML v subsystému WPF
<a name="introduction"></a>Kód na pozadí je termín, který se používá k popisu kódu, který je spojen s objekty definovanými značkou, když [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránka je kompilována kódu. Toto téma popisuje požadavky na pozadí kódu a také alternativní mechanismus vloženého kódu pro kód v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Toto téma obsahuje následující oddíly:  
  
- [Požadavky](#Prerequisites)  
  
- [Kód na pozadí a jazyk XAML](#codebehind_and_the_xaml_language)  
  
- [Kód na pozadí, obslužná rutina události a požadavky na částečnou třídu v subsystému WPF](#Code_behind__Event_Handler__and_Partial_Class)  
  
- [x:Code](#x_Code)  
  
- [Omezení vloženého kódu](#Inline_Code_Limitations)  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že jste si přečetli [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md) a máte základní znalosti CLR a objektově orientovaného programování.  
  
<a name="codebehind_and_the_xaml_language"></a>   
## <a name="code-behind-and-the-xaml-language"></a>Kód na pozadí a jazyk XAML  
 Jazyk XAML obsahuje funkce na úrovni jazyka, které umožňují přidružit soubory kódu k souborům značek ze strany souboru značek. Konkrétně jazyk XAML definuje direktivy [X:Class direktivy](../../../desktop-wpf/xaml-services/xclass-directive.md)jazyka, direktiva [x:Subclass –](../../../desktop-wpf/xaml-services/xsubclass-directive.md)a [direktiva x:ClassModifier –](../../../desktop-wpf/xaml-services/xclassmodifier-directive.md). Přesně způsob, jak by měl být kód vytvořen a jak integrovat značky a kód, není součástí jazyka XAML. Je ponecháno až do architektury, jako je WPF, k určení, jak integrovat kód, jak použít XAML v aplikacích a programovacích modelech a akce sestavení nebo jiná podpora, kterou vyžaduje.  
  
<a name="Code_behind__Event_Handler__and_Partial_Class"></a>   
## <a name="code-behind-event-handler-and-partial-class-requirements-in-wpf"></a>Kód na pozadí, obslužná rutina události a požadavky na částečnou třídu v subsystému WPF  
  
- Částečná třída musí být odvozena od typu, který zálohuje kořenový element.  
  
- Všimněte si, že pod výchozím chováním akcí sestavení kompilace kódu můžete nechat odvození prázdné v definici částečné třídy na straně kódu na pozadí. Zkompilovaný výsledek bude předpokládat, že typ zálohování kořene stránky bude základem pro částečnou třídu, a to i v případě, že není zadaný. Spoléhání se na toto chování však není osvědčeným postupem.  
  
- Obslužné rutiny událostí, které zapisujete do kódu na pozadí, musí být instanční metody a nemohou být statickými metodami. Tyto metody musí být definovány částečnou třídou v oboru názvů CLR identifikovaném pomocí `x:Class`. Nelze kvalifikovat název obslužné rutiny události, aby [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor mohl vyhledat obslužnou rutinu události pro zapojení událostí v jiném oboru třídy.  
  
- Obslužná rutina musí odpovídat delegátovi pro příslušnou událost v systému typů zálohování.  
  
- Pro jazyk Microsoft Visual Basic konkrétně můžete použít klíčové slovo `Handles` pro konkrétní jazyk k přidružení obslužných rutin s instancemi a událostmi v deklaraci obslužné rutiny namísto připojení obslužných rutin s atributy v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Tato technika ale má určitá omezení, protože klíčová slova `Handles` nepodporují všechny konkrétní funkce systému událostí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], jako jsou například určité scénáře směrované události nebo připojené události. Podrobnosti najdete v tématu [Visual Basic a zpracování událostí WPF](visual-basic-and-wpf-event-handling.md).  
  
<a name="x_Code"></a>   
## <a name="xcode"></a>x:Code  
 [x:Code](../../../desktop-wpf/xaml-services/xcode-intrinsic-xaml-type.md) je element direktivy definovaný v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Element direktivy `x:Code` může obsahovat vložený programovací kód. Kód, který je definovaný jako vložený, může komunikovat s [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] na stejné stránce. Následující příklad znázorňuje vložený C# kód. Všimněte si, že kód je uvnitř elementu `x:Code` a že kód musí být uzavřený pomocí `<CDATA[`...`]]>` k úniku obsahu pro XML, takže procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (interpretace schématu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nebo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] schématu) se nepokusí interpretovat obsah doslova jako XML.  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithInlineCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page4.xaml#buttonwithinlinecode)]  
  
<a name="Inline_Code_Limitations"></a>   
## <a name="inline-code-limitations"></a>Omezení vloženého kódu  
 Měli byste zvážit vyloučení nebo omezení použití vloženého kódu. V souvislosti s architekturou a kódováním filozofie udržování oddělení značek a kódu na pozadí udržuje role návrháře a vývojářů mnohem obecnější. Na pokročilejší úrovni může být kód, který píšete pro vložený kód, nevhodný pro zápis, protože jste vždy zapsáni do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] vygenerované částečné třídy a lze použít pouze výchozí mapování oboru názvů XML. Vzhledem k tomu, že nemůžete přidat příkazy `using`, je nutné plně kvalifikovat mnoho volání rozhraní API, které provedete. Výchozí mapování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zahrnují většinu, ale ne všechny obory názvů CLR, které jsou k dispozici v sestaveních [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]; budete muset plně kvalifikovat volání typů a členů obsažených v jiných oborech názvů CLR. Nemůžete také definovat cokoli nad částečnou třídou ve vloženém kódu a všechny entity uživatelského kódu, na které odkazujete, musí existovat jako člen nebo proměnná v rámci generované částečné třídy. Jiné funkce programování specifické pro konkrétní jazyk, například makra nebo `#ifdef` proti globálním proměnným nebo proměnným sestavení, nejsou k dispozici ani. Další informace najdete v tématu [vnitřní typ XAML x:Code](../../../desktop-wpf/xaml-services/xcode-intrinsic-xaml-type.md).  
  
## <a name="see-also"></a>Viz také:

- [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [x:Code – vnitřní typ jazyka XAML](../../../desktop-wpf/xaml-services/xcode-intrinsic-xaml-type.md)
- [Sestavení aplikace WPF](../app-development/building-a-wpf-application-wpf.md)
- [Podrobná syntaxe XAML](xaml-syntax-in-detail.md)
