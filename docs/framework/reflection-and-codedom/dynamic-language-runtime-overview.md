---
title: Dynamic Language Runtime přehled | Dokumentace Microsoftu
ms.date: 03/30/2017
helpviewer_keywords:
- dynamic language runtime
- IronPython
- DLR
- IronRuby
ms.assetid: f769a271-8aff-4bea-bfab-6160217ce23d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a4645efc9276429cbdb0812f1ca501c89ea5dbb
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43855149"
---
# <a name="dynamic-language-runtime-overview"></a>Přehled DLR (Dynamic Language Runtime)
*Dynamickým jazykovým modulem runtime* (DLR) je prostředí modulu runtime, který přidá sadu služeb pro dynamické jazyky common language runtime (CLR). DLR usnadňuje vývoj dynamické jazyky spustit na rozhraní .NET Framework a přidat dynamické funkce pro staticky typu jazyky.  
  
 Dynamické jazyky můžete identifikovat typ objektu v době běhu, zatímco v staticky zadali jazyků, jako je C# a Visual Basic (při použití `Option Explicit On`) je nutné zadat typy objektů v době návrhu. Příklady dynamické jazyky jsou Lisp, Smalltalk, JavaScript, PHP, Ruby, Python, ColdFusion, Lua, Cobra a technologii Groovy.  
  
 Většina dynamické jazyky poskytují následující výhody pro vývojáře:  
  
-   Možnost používat rychlé zpětné vazby (REPL nebo čtení vyhodnocení print smyčky). To vám umožní zadat několik příkazů a okamžitě je pro zobrazení výsledků spuštění.  
  
-   Podpora pro vývoj shora dolů a více tradičních vývojových zdola nahoru. Například při použití s přístupem shora dolů, můžete volat funkce, které ještě nejsou naimplementované a pak přidejte základní implementace, když je potřebujete.  
  
-   Snadnější Refaktoring a kód změny, protože není potřeba změnit deklarace statického typu v rámci kódu.  
  
 Ujistěte se, dynamické jazyky vynikající skriptovací jazyky. Zákazníci můžou snadno rozšířit aplikace vytvořené s použitím dynamické jazyky se nové příkazy a funkce. Dynamické jazyky se také často používají pro vytváření webů a otestujte postroje zachování serverových farem, různé nástroje pro vývoj a provedením transformace dat.  
  
 Účelem DLR je chcete povolit režim dynamické jazyky pro spuštění na rozhraní .NET Framework a udělit jim interoperabilitě .NET. DLR představuje dynamické objekty jazyka C# a Visual Basic v sadě Visual Studio 2010 pro podporu dynamické chování v těchto jazycích a povolení jejich vzájemná spolupráce s dynamické jazyky.  
  
 DLR také vám pomůže vytvořit knihovny, které podporují dynamické operace. Například pokud máte knihovnu, která používá objekty jazyka XML nebo JavaScript Object Notation (JSON), může zobrazit objekty jako dynamické objekty pro jazyky, které používají DLR. To umožňuje uživatelům knihovny psát syntakticky jednodušší a přirozenější kód pro provoz s objekty a přístup ke členům objektu.  
  
 Například můžete použít následující kód pro zvýšení čítače v kódu XML v jazyce C#.  
  
 `Scriptobj.SetProperty("Count", ((int)GetProperty("Count")) + 1);`  
  
 Pomocí DLR, můžete místo toho použít následující kód pro stejnou operaci.  
  
 `scriptobj.Count += 1;`  
  
 Stejně jako modul CLR DLR je součástí rozhraní .NET Framework a je součástí instalačních balíčků rozhraní .NET Framework a sady Visual Studio. Verze open source DLR je také k dispozici ke stažení [IronLanguages/dlr](https://github.com/IronLanguages/dlr) úložišti na Githubu.  
  
> [!NOTE]
>  Verze open source DLR má všechny funkce DLR, který je součástí sady Visual Studio a rozhraní .NET Framework. Poskytuje také další podporu pro vývojáře jazyka. Další informace najdete v dokumentaci na [IronLanguages/dlr](https://github.com/IronLanguages/dlr) úložišti na Githubu. 
  
 Příklady vyvinuté pomocí DLR jazyky patří:  
  
-   Ironpythonu. K dispozici jako open source softwaru z [Githubu](https://github.com/IronLanguages/ironpython2) webu.  
  
-   IronRuby. K dispozici jako open source softwaru z [RubyForge](https://go.microsoft.com/fwlink/?LinkId=141044) webu.  
  
## <a name="primary-dlr-advantages"></a>Primární DLR výhody  
 DLR nabízí následující výhody.  
  
### <a name="simplifies-porting-dynamic-languages-to-the-net-framework"></a>Zjednodušuje portování dynamické jazyky rozhraní .NET Framework  
 DLR umožňuje jazyk implementátory vyhnout se vytváření lexikální analyzátory, analyzátorů, sémantické analyzátory, generátory kódu a dalších nástrojů, které se tradičně bylo nutné vytvořit sami. Použití DLR, je potřeba jazyk vytvořit *stromů výrazů*, které představují kódu na úrovni jazyka ve struktuře ve tvaru stromu pomocné rutiny modulu runtime, a volitelné dynamické objekty, které implementují <xref:System.Dynamic.IDynamicMetaObjectProvider> rozhraní. DLR a rozhraní .NET Framework můžete automatizovat spoustu analýzu kódu a úkolů generování kódu. To umožňuje jazyk implementátory soustředit na funkce jedinečný jazyka.  
  
### <a name="enables-dynamic-features-in-statically-typed-languages"></a>Umožňuje dynamické funkce ve staticky zadávané jazyky  
 Existující jazycích rozhraní .NET Framework, jako je C# a Visual Basic můžete vytvářet dynamické objekty a jejich použití spolu s staticky typované objekty. Například C# a Visual Basic můžete použít dynamické objekty pro účely reflexe HTML Document Object Model (DOM) a .NET.  
  
### <a name="provides-future-benefits-of-the-dlr-and-net-framework"></a>Poskytuje další výhody DLR a rozhraní .NET Framework  
 Jazyky, které jsou implementovány pomocí DLR využívat budoucí vylepšení DLR a rozhraní .NET Framework. Například pokud vyjde nová verze rozhraní .NET Framework novou verzi, která má lepší systému uvolňování paměti nebo rychlejší načítání čas sestavení, jazyky, které jsou implementovány pomocí DLR okamžitě využívat stejné výhody. Pokud DLR přidá optimalizace, například lepší kompilace, se pro všechny jazyky, které jsou implementovány pomocí DLR také zlepšuje výkon.  
  
### <a name="enables-sharing-of-libraries-and-objects"></a>Povolí sdílení knihovny a objektů  
 Objekty a knihovny, které jsou implementované v jednom jazyce lze použít v jiných jazycích. DLR taky umožňuje spolupráci mezi staticky typové a dynamické jazyky. Například C# lze deklarovat dynamický objekt, který používá knihovnu, která je napsána v jazyce dynamické. Ve stejnou dobu můžete používat dynamické jazyky knihovny z rozhraní .NET Framework.  
  
### <a name="provides-fast-dynamic-dispatch-and-invocation"></a>Poskytuje rychlé dynamické odeslání a volání  
 DLR poskytuje rychlé spuštění dynamické operace díky podpoře rozšířeného polymorfní ukládání do mezipaměti. DLR vytvoří pravidla pro vazby operace, které používají objekty pro implementace modulu runtime potřebné a pak ukládá do mezipaměti, tato pravidla, aby se zabránilo vyčerpáním prostředků výpočty vazbu během po sobě jdoucích spuštěních stejný kód na stejné typy objektů.  
  
## <a name="dlr-architecture"></a>Architektura DLR  
 Následující obrázek ukazuje architekturu dynamickým jazykovým modulem runtime.  
  
 ![Přehled Dynamic Language Runtime architektury](../../../docs/framework/reflection-and-codedom/media/dlr-archoverview.png "DLR_ArchOverview")  
Architektura DLR  
  
 DLR přidá sadu služeb pro modul CLR pro lepší podporuje dynamické jazyky. Tyto služby patří:  
  
-   Stromy výrazů. DLR používá stromů výrazů k reprezentaci sémantiku jazyka. Pro tento účel DLR má rozšířené stromům výrazů LINQ tok řízení, přiřazení a ostatní uzly jazykové modelování. Další informace najdete v tématu [stromů výrazů](https://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b).  
  
-   Volání, ukládání do mezipaměti webu. A *dynamického volání webu* je místo, kde v kódu, kde provádět operace jako `a + b` nebo `a.b()` na dynamické objekty. DLR ukládá do mezipaměti charakteristiky `a` a `b` (obvykle typy tyto objekty) a informace o operaci. Pokud tato operace byla provedena dříve DLR načte všechny potřebné informace z mezipaměti pro odesílání rychlá.  
  
-   Vzájemná funkční spolupráce dynamický objekt. DLR poskytuje sadu tříd a rozhraní, které představují dynamických objektů a operací a nemůže použít jiný jazyk implementátory a autoři dynamické knihovny. Tyto třídy a rozhraní zahrnují <xref:System.Dynamic.IDynamicMetaObjectProvider>, <xref:System.Dynamic.DynamicMetaObject>, <xref:System.Dynamic.DynamicObject>, a <xref:System.Dynamic.ExpandoObject>.  
  
 DLR používá vazače lokalit volání komunikovat pouze s použitím rozhraní .NET Framework, ale s jinými infrastruktur a služeb, včetně technologie Silverlight a modulu COM. Vazače zapouzdření sémantika jazyka a určete, jak k provádění operací v lokalitě volání pomocí stromů výrazů. Díky tomu dynamické a jazyky, které používají DLR ke sdílení knihovny a získání přístupu k všechny technologie, které podporuje DLR staticky zadali.  
  
## <a name="dlr-documentation"></a>Dokumentace ke službě DLR  
 Další informace o tom, jak používat open source verze DLR přidat dynamické chování pro jazyk, nebo o tom, jak povolit použití dynamické jazyce s využitím rozhraní .NET Framework naleznete v dokumentaci na [IronLanguages/dlr](https://github.com/IronLanguages/dlr/tree/master/Docs) úložiště na Githubu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Dynamic.ExpandoObject>  
 <xref:System.Dynamic.DynamicObject>  
 [Modul Common Language Runtime](../../../docs/standard/clr.md)  
 [Stromy výrazů](https://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)  
 [Návod: Vytváření a používání dynamických objektů](~/docs/csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
