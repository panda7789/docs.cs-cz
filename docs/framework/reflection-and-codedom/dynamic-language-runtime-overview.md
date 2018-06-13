---
title: Dynamic Language Runtime přehled | Microsoft Docs
ms.date: 03/30/2017
helpviewer_keywords:
- dynamic language runtime
- IronPython
- DLR
- IronRuby
ms.assetid: f769a271-8aff-4bea-bfab-6160217ce23d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 09cd345daffa2418b33f032e8bab47c81e2a8526
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397283"
---
# <a name="dynamic-language-runtime-overview"></a>Přehled DLR (Dynamic Language Runtime)
*Dynamické běhové* (DLR) je prostředí runtime, který přidává sadu služeb pro dynamické jazyky do common language runtime (CLR). DLR usnadňuje vývoj dynamických jazyků pro spuštění na rozhraní .NET Framework a přidat dynamické funkce do staticky zadávané jazyky.  
  
 Dynamické jazyky můžete identifikovat typ objektu v době běhu, zatímco v staticky zadali jazyků, například C# a Visual Basic (při použití `Option Explicit On`) je nutné zadat typy objektů v době návrhu. Příkladem dynamické jazyky jsou Lisp, Smalltalk, JavaScript, PHP, Ruby, Python, ColdFusion, Lua, Cobra a Groovy.  
  
 Většina dynamických jazyky poskytují pro vývojáře má následující výhody:  
  
-   Možnost používat rychlé zpětné vazby (REPL nebo pro čtení vyhodnotit tiskových smyčky). To vám umožní zadat několik příkazy a okamžitě provést je zobrazit výsledky.  
  
-   Podporu pro vývoj vertikální i tradičnější vývoj zdola nahoru. Například při použití přístupu shora dolů, můžete volat funkce, které zatím nejsou implementovány a poté přidejte základní implementace, když je potřebujete.  
  
-   Snadnější Refaktoring a kódu změny, protože není nutné změnit statický typ deklarace napříč kódem.  
  
 Dynamické jazyky zkontrolujte vynikající skriptovací jazyky. Zákazníci můžou snadno rozšířit aplikace vytvořené pomocí dynamických jazyků s nové příkazy a funkce. Dynamické jazyky se také často používají pro vytváření webů a testování nevodivou údržby serverové farmy, vývoj různých nástrojů a transformace dat provádění.  
  
 Účelem DLR je umožnit systém dynamických jazyků pro spuštění na rozhraní .NET Framework a jim poskytnout interoperabilitě .NET. DLR zavádí dynamických objektů jazyka C# a Visual Basic v sadě Visual Studio 2010 podporu v těchto jazycích dynamické chování a povolení jejich vzájemná spolupráce pomocí dynamických jazyků.  
  
 DLR také vám pomůže vytvořit knihovny, které podporují dynamické operace. Například pokud máte knihovnu, která používá XML nebo JavaScript Object Notation (JSON) objektů, vašich objektů může se objevit jako dynamické objekty pro jazyky, které používají DLR. Díky tomu mají uživatelé knihovny napsat syntakticky jednodušší a přirozenější kód pro provoz se objekty a přístup ke členům objektu.  
  
 Například můžete použít následující kód se zvýší čítače v XML v jazyce C#.  
  
 `Scriptobj.SetProperty("Count", ((int)GetProperty("Count")) + 1);`  
  
 Pomocí DLR, můžete místo toho použít následující kód pro stejnou operaci.  
  
 `scriptobj.Count += 1;`  
  
 Jako modulu CLR DLR je součástí rozhraní .NET Framework a je součástí instalačních balíčků rozhraní .NET Framework a Visual Studio. Open-source verze DLR je také k dispozici ke stažení na [IronLanguages/dlr](https://github.com/IronLanguages/dlr) úložišti na Githubu.  
  
> [!NOTE]
>  Open-source verze DLR obsahuje všechny funkce DLR, která je obsažena v sadě Visual Studio a rozhraní .NET Framework. Poskytuje také další podporu pro jazyk implementátory informačních technologií. Další informace najdete v dokumentaci na [IronLanguages/dlr](https://github.com/IronLanguages/dlr) úložišti na Githubu. 
  
 Příklady jazyky vyvinuté pomocí DLR zahrnují následující:  
  
-   IronPython. K dispozici jako open-source softwaru z [Githubu](https://github.com/IronLanguages/ironpython2) webu.  
  
-   IronRuby. K dispozici jako open-source softwaru z [RubyForge](http://go.microsoft.com/fwlink/?LinkId=141044) webu.  
  
## <a name="primary-dlr-advantages"></a>Primární výhody DLR  
 DLR nabízí následující výhody.  
  
### <a name="simplifies-porting-dynamic-languages-to-the-net-framework"></a>Zjednodušuje portování dynamické jazyky rozhraní .NET Framework  
 DLR umožňuje implementátory jazyk pro Vyhněte se vytváření lexikální analyzátory, analyzátory, sémantického analyzátorů, generátory kódu a jiné nástroje, které tradičně měly vytvořit sami. Pokud chcete používat DLR, jazyk potřebuje k vytvoření *stromů výrazů*, které představují úroveň jazyka kódu do ve tvaru stromové struktury, runtime pomocné rutiny, a volitelné dynamické objekty, které implementovat <xref:System.Dynamic.IDynamicMetaObjectProvider> rozhraní. DLR a rozhraní .NET Framework automatizovat spoustu analýza kódu a úlohy generování kódu. To umožňuje jazyk implementátory soustředit se na funkce jedinečný jazyka.  
  
### <a name="enables-dynamic-features-in-statically-typed-languages"></a>Umožňuje dynamické funkce v staticky zadávané jazyky  
 Existující jazyky rozhraní .NET Framework, jako je například C# a Visual Basic můžete vytvářet dynamické objekty a použít je spolu s objektů staticky typem. Například C# a Visual Basic můžete použít dynamické objekty pro reflexi jazyka HTML, Document Object (Model DOM) a rozhraní .NET.  
  
### <a name="provides-future-benefits-of-the-dlr-and-net-framework"></a>Poskytuje budoucí výhody DLR a rozhraní .NET Framework  
 Jazyky, které jsou implementovány pomocí DLR využívat výhod budoucí vylepšení DLR a rozhraní .NET Framework. Například pokud rozhraní .NET Framework verze nové verze, která má lepší uvolňování paměti nebo rychlejší sestavení čas načítání, jazyky implementovaná pomocí DLR okamžitě získat stejné výhody. Pokud DLR přidá optimalizace například lepší kompilace, se pro všechny jazyky, které jsou implementovány pomocí DLR také zlepšuje výkon.  
  
### <a name="enables-sharing-of-libraries-and-objects"></a>Umožňuje sdílení knihovny a objektů  
 Objekty a knihovny, které jsou implementované v jednom jazyce lze další jazyky. DLR taky umožňuje vzájemná spolupráce mezi jazyky staticky typové a dynamické. Například C# lze deklarovat dynamický objekt, který používá knihovnu dynamické jazyk. Ve stejnou dobu můžete použít dynamické jazyky knihoven z rozhraní .NET Framework.  
  
### <a name="provides-fast-dynamic-dispatch-and-invocation"></a>Poskytuje rychlé dynamického odeslání a volání  
 DLR poskytuje rychlé spuštění dynamické operace díky podpoře rozšířeného polymorfní ukládání do mezipaměti. DLR vytvoří pravidla pro vazby operace, které používají objekty, které se implementace nezbytné runtime a pak ukládá do mezipaměti, tato pravidla, aby se zabránilo vyčerpáním prostředků výpočty vazba během následných spuštěních stejný kód na stejné typy objektů.  
  
## <a name="dlr-architecture"></a>Architektura DLR  
 Následující obrázek znázorňuje architekturu dynamické language runtime.  
  
 ![Přehled Dynamic Language Runtime architektury](../../../docs/framework/reflection-and-codedom/media/dlr-archoverview.png "DLR_ArchOverview")  
Architektura DLR  
  
 DLR přidává do modulu CLR pro lepší sadu služeb podporující dynamické jazyky. Tyto služby patří:  
  
-   Stromy výrazů. DLR používá stromů výrazů k reprezentaci sémantiku jazyka. Pro tento účel DLR má rozšířené stromů výrazů LINQ tok řízení, přiřazení a dalších uzlů modelování jazyk. Další informace najdete v tématu [stromů výrazů](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b).  
  
-   Volání lokality ukládání do mezipaměti. A *dynamické volání lokality* je místo v kódu, kde provádět operace jako `a + b` nebo `a.b()` na dynamické objekty. DLR ukládá do mezipaměti charakteristika `a` a `b` (obvykle typy tyto objekty) a informace o operaci. Pokud takovou operaci nebylo provedeno dříve, DLR načte všechny potřebné informace z mezipaměti pro rychlé odesílání.  
  
-   Interoperabilita dynamický objekt. DLR poskytuje sadu třídy a rozhraní, které představují dynamické objekty a operace a mohou být využívána implementátory jazyk a autoři dynamické knihovny. Tyto třídy a rozhraní zahrnují <xref:System.Dynamic.IDynamicMetaObjectProvider>, <xref:System.Dynamic.DynamicMetaObject>, <xref:System.Dynamic.DynamicObject>, a <xref:System.Dynamic.ExpandoObject>.  
  
 DLR používá vazače v lokalitách volání komunikovat pouze s rozhraním .NET Framework, ale s dalšími infrastruktury a službami, včetně Silverlight a COM. Vazače zapouzdření sémantiku tohoto jazyka a určete, jak k provádění operací na volání webu pomocí stromů výrazů. To umožňuje dynamické a jazyky, které používají DLR do sdílené složky knihovny a získání přístupu k všechny technologie, které podporuje DLR staticky zadali.  
  
## <a name="dlr-documentation"></a>DLR dokumentace  
 Další informace o tom, jak používat s otevřeným zdrojem verzi DLR přidat dynamické chování pro jazyk, nebo o tom, jak povolit použití dynamické jazyka s rozhraním .NET Framework, najdete v dokumentaci na [IronLanguages/dlr](https://github.com/IronLanguages/dlr/tree/master/Docs) úložišti na Githubu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Dynamic.ExpandoObject>  
 <xref:System.Dynamic.DynamicObject>  
 [Modul Common Language Runtime](../../../docs/standard/clr.md)  
 [Stromy výrazů](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)  
 [Návod: Vytváření a používání dynamických objektů](~/docs/csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
