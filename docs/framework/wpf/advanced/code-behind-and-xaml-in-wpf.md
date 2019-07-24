---
title: Podkladový kód a kód XAML v subsystému WPF
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], code-behind
- code-behind files [WPF], XAML
ms.assetid: 9df6d3c9-aed3-471c-af36-6859b19d999f
ms.openlocfilehash: acd8c9ff0a4ff718dba272958a3e63820bcf1354
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401605"
---
# <a name="code-behind-and-xaml-in-wpf"></a>Podkladový kód a kód XAML v subsystému WPF
<a name="introduction"></a>Kód na pozadí je termín, který se používá k popisu kódu, který je spojen s objekty definovanými značkou [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , když je stránka kompilována značek. Toto téma popisuje požadavky na pozadí kódu a také alternativní mechanismus vloženého kódu pro kód v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Toto téma obsahuje následující oddíly:  
  
- [Požadavky](#Prerequisites)  
  
- [Kód na pozadí a jazyk XAML](#codebehind_and_the_xaml_language)  
  
- [Kód na pozadí, obslužná rutina události a požadavky na částečnou třídu v subsystému WPF](#Code_behind__Event_Handler__and_Partial_Class)  
  
- [x:Code](#x_Code)  
  
- [Omezení vloženého kódu](#Inline_Code_Limitations)  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že jste si přečetli [Přehled XAML (WPF)](xaml-overview-wpf.md) a máte základní znalosti CLR a objektově orientovaného programování.  
  
<a name="codebehind_and_the_xaml_language"></a>   
## <a name="code-behind-and-the-xaml-language"></a>Kód na pozadí a jazyk XAML  
 Jazyk XAML obsahuje funkce na úrovni jazyka, které umožňují přidružit soubory kódu k souborům značek ze strany souboru značek. Konkrétně jazyk XAML definuje direktivy [X:Class direktivy](../../xaml-services/x-class-directive.md)jazyka, direktiva [x:Subclass –](../../xaml-services/x-subclass-directive.md)a [direktiva x:ClassModifier –](../../xaml-services/x-classmodifier-directive.md). Přesně způsob, jak by měl být kód vytvořen a jak integrovat značky a kód, není součástí jazyka XAML. Je ponecháno až do architektury, jako je WPF, k určení, jak integrovat kód, jak použít XAML v aplikacích a programovacích modelech a akce sestavení nebo jiná podpora, kterou vyžaduje.  
  
<a name="Code_behind__Event_Handler__and_Partial_Class"></a>   
## <a name="code-behind-event-handler-and-partial-class-requirements-in-wpf"></a>Kód na pozadí, obslužná rutina události a požadavky na částečnou třídu v subsystému WPF  
  
- Částečná třída musí být odvozena od typu, který zálohuje kořenový element.  
  
- Všimněte si, že pod výchozím chováním akcí sestavení kompilace kódu můžete nechat odvození prázdné v definici částečné třídy na straně kódu na pozadí. Zkompilovaný výsledek bude předpokládat, že typ zálohování kořene stránky bude základem pro částečnou třídu, a to i v případě, že není zadaný. Spoléhání se na toto chování však není osvědčeným postupem.  
  
- Obslužné rutiny událostí, které zapisujete do kódu na pozadí, musí být instanční metody a nemohou být statickými metodami. Tyto metody musí být definovány částečnou třídou v oboru názvů CLR, který `x:Class`identifikuje. Nelze kvalifikovat název obslužné rutiny události, aby [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] mohl procesor vyhledat obslužnou rutinu události pro zapojení událostí v jiném oboru třídy.  
  
- Obslužná rutina musí odpovídat delegátovi pro příslušnou událost v systému typů zálohování.  
  
- Pro jazyk Microsoft Visual Basic konkrétně můžete použít klíčové slovo specifické `Handles` pro přidružení obslužných rutin s instancemi a událostmi v deklaraci obslužné rutiny namísto připojení obslužných rutin s atributy v. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Tato technika ale má určitá omezení, protože `Handles` klíčové slovo nemůže podporovat všechny konkrétní funkce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systému událostí, jako jsou například určité scénáře směrované události nebo připojené události. Podrobnosti najdete v tématu [Visual Basic a zpracování událostí WPF](visual-basic-and-wpf-event-handling.md).  
  
<a name="x_Code"></a>   
## <a name="xcode"></a>x:Code  
 [x:Code](../../xaml-services/x-code-intrinsic-xaml-type.md) je element direktivy definované v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Element `x:Code` direktivy může obsahovat vložený programovací kód. Kód, který je definovaný jako [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] vložený, může pracovat se stejnou stránkou. Následující příklad znázorňuje vložený C# kód. Všimněte si, že kód je uvnitř `x:Code` elementu a že kód musí být ohraničen `<CDATA[`... [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]Chcete-li odblokovat obsah pro, aby procesor (interpretace schématu nebo schématu) nepokusí o interpretaci obsahu doslova jako. `]]>`  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithInlineCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page4.xaml#buttonwithinlinecode)]  
  
<a name="Inline_Code_Limitations"></a>   
## <a name="inline-code-limitations"></a>Omezení vloženého kódu  
 Měli byste zvážit vyloučení nebo omezení použití vloženého kódu. V souvislosti s architekturou a kódováním filozofie udržování oddělení značek a kódu na pozadí udržuje role návrháře a vývojářů mnohem obecnější. Na pokročilejší úrovni může být kód, který píšete pro vložený kód, nevhodný pro zápis, protože jste vždy zapsáni do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] generované částečné třídy a lze použít pouze výchozí mapování oboru názvů XML. Vzhledem k tomu, `using` že nemůžete přidávat příkazy, je nutné plně kvalifikovat mnoho volání rozhraní API, které provedete. Výchozí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mapování zahrnují většinu oborů názvů CLR, které jsou přítomny [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v sestaveních. k plnému kvalifikovanému volání typů a členů obsažených v jiných oborech názvů CLR se bude muset plně kvalifikovat. Nemůžete také definovat cokoli nad částečnou třídou ve vloženém kódu a všechny entity uživatelského kódu, na které odkazujete, musí existovat jako člen nebo proměnná v rámci generované částečné třídy. Jiné funkce programování specifické pro konkrétní jazyk, jako jsou `#ifdef` například makra nebo proti globálním proměnným nebo proměnným sestavení, nejsou k dispozici ani. Další informace najdete v tématu [vnitřní typ XAML x:Code](../../xaml-services/x-code-intrinsic-xaml-type.md).  
  
## <a name="see-also"></a>Viz také:

- [Přehled XAML (WPF)](xaml-overview-wpf.md)
- [x:Code – vnitřní typ jazyka XAML](../../xaml-services/x-code-intrinsic-xaml-type.md)
- [Sestavení aplikace WPF](../app-development/building-a-wpf-application-wpf.md)
- [Podrobná syntaxe XAML](xaml-syntax-in-detail.md)
