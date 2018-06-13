---
title: Použití typu dynamic (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic [C#], about dynamic type
- dynamic type [C#]
ms.assetid: 3828989d-c967-4a51-b948-857ebc8fdf26
ms.openlocfilehash: 67eb39fd6f2077d2adf1d38d001e801b815d687d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33336635"
---
# <a name="using-type-dynamic-c-programming-guide"></a>Použití typu dynamic (Průvodce programováním v C#)
[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] zavádí nový typ `dynamic`. Typ je statický typu, ale objekt typu `dynamic` obchází Kontrola statické typu. Ve většině případů funguje stejně, jako má typ `object`. Při kompilaci, element, který je zadán jako `dynamic` se předpokládá, že pro podporu všechny operace. Proto není nutné starat o tom, zda objekt získá svou hodnotu z rozhraní API modelu COM, dynamické jazyce například IronPython, z HTML Document Object Model (DOM), z reflexe nebo z jinde v programu. Ale pokud kód není platný, jsou zachyceny chyby za běhu.  
  
 Například pokud metodu instance `exampleMethod1` v následujícím kódu má jenom jeden parametr, kompilátor rozpozná, první volání metody, `ec.exampleMethod1(10, 4)`, není platný, protože obsahuje dva argumenty. Volání způsobí, že chyba kompilátoru. Druhé volání metody, `dynamic_ec.exampleMethod1(10, 4)`, kontrolována kompilátorem, protože typ `dynamic_ec` je `dynamic`. Proto je uvedená žádná chyba kompilátoru. Však chyba není vyhnuli oznámení po neomezenou dobu. To je zachycena v době běhu a způsobí spuštění výjimky.  
  
 [!code-csharp[CsProgGuideTypes#50](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_1.cs)]  
  
 [!code-csharp[CsProgGuideTypes#56](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_2.cs)]  
  
 Role kompilátoru v těchto příkladech je do balíčku společně informace o každý příkaz navržení udělat, aby objekt nebo výraz, který je zadán jako `dynamic`. Za běhu je zkontrolován uložené informace a žádnému příkazu, který není platný způsobí spuštění výjimky.  
  
 Výsledek nejvíce dynamické operace je sám `dynamic`. Například, pokud se ukazatel myši nad použití `testSum` v následujícím příkladu, IntelliSense zobrazí typ **(místní proměnné) dynamické testSum**.  
  
 [!code-csharp[CsProgGuideTypes#51](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_3.cs)]  
  
 Operace, ve kterých je výsledek `dynamic` obsahovat převody z `dynamic` jiný typ, a volá konstruktor, které zahrnují argumenty typu `dynamic`. Například typ `testInstance` v toto prohlášení je `ExampleClass`, nikoli `dynamic`.  
  
 [!code-csharp[CsProgGuideTypes#52](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_4.cs)]  
  
 Převod příklady jsou uvedeny v následující části "Převody."  
  
## <a name="conversions"></a>Převody  
 Převody mezi dynamické objekty a jinými typy jsou snadné. To umožňuje vývojáři přepínat mezi chování dynamické a bez dynamické.  
  
 Jakýkoli objekt můžete převést na dynamický typ implicitně, jak je znázorněno v následujících příkladech.  
  
 [!code-csharp[CsProgGuideTypes#53](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_5.cs)]  
  
 Naopak implicitní převod můžete dynamicky uplatňují na jakýkoli výraz typu `dynamic`.  
  
 [!code-csharp[CsProgGuideTypes#54](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_6.cs)]  
  
## <a name="overload-resolution-with-arguments-of-type-dynamic"></a>Řešení s argumenty z typu dynamic přetížení  
 K rozlišení přetížení v době běhu místo v době kompilace dojde, pokud jeden nebo více argumentů volání metody mít typ `dynamic`, nebo pokud příjemce volání metody, které je typu `dynamic`. V následujícím příkladu pokud dostupné jenom `exampleMethod2` provést argument řetězce je definována metoda odesílání `d1` jako argument nezpůsobí Chyba kompilátoru, ale způsobit spuštění výjimka. Řešení přetížení nezdaří za běhu, protože běhu typ `d1` je `int`, a `exampleMethod2` vyžaduje řetězec.  
  
 [!code-csharp[CsProgGuideTypes#55](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_7.cs)]  
  
## <a name="dynamic-language-runtime"></a>Dynamic Language Runtime  
 Dynamické language runtime (DLR) je nové rozhraní API v [!INCLUDE[net_v40_short](~/includes/net-v40-short-md.md)]. Poskytuje infrastrukturu, která podporuje `dynamic` typu v C# a také provádění dynamické programovacích jazyků, jako je například IronPython a IronRuby. Další informace o DLR najdete v tématu [přehled dynamického modulu Runtime jazyka](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).  
  
## <a name="com-interop"></a>Zprostředkovatel komunikace s objekty COM  
 [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] zahrnuje několik funkcí, které lepší spolupráce se rozhraní API modelu COM, jako je například rozhraní API Office automatizace. Mezi vylepšení patří použití `dynamic` typ a [pojmenované a nepovinné argumenty](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md).  
  
 Mnoho způsobů COM povolit jevu ve typy argumentů a návratový typ tak, že určíte typy jako `object`. To je nezbytné explicitní přetypování hodnoty, které mají společně se silným typem proměnné v jazyce C#. Pokud zkompilujete pomocí [/Link (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/link-compiler-option.md) možnost zavedení `dynamic` typu umožňuje považovat výskytů `object` v modelu COM podpisy jako kdyby byly typu `dynamic`a tím aby se zabránilo mnohem přetypování. Například následující příkazy kontrastu přístupu buňku v tabulce aplikace Microsoft Office Excel s `dynamic` typu a bez `dynamic` typu.  
  
 [!code-csharp[csOfficeWalkthrough#12](../../../csharp/programming-guide/interop/codesnippet/CSharp/using-type-dynamic_8.cs)]  
  
 [!code-csharp[csOfficeWalkthrough#13](../../../csharp/programming-guide/interop/codesnippet/CSharp/using-type-dynamic_9.cs)]  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[dynamic](../../../csharp/language-reference/keywords/dynamic.md)|Popisuje použití `dynamic` – klíčové slovo.|  
|[Přehled DLR (Dynamic Language Runtime)](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)|Poskytuje přehled DLR, což je prostředí runtime, který přidává sadu služeb pro dynamické jazyky do common language runtime (CLR).|  
|[Návod: Vytváření a používání dynamických objektů](../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)|Poskytuje podrobné pokyny pro vytvoření vlastní dynamický objekt a pro vytvoření projektu, který přistupuje `IronPython` knihovny.|  
|[Postupy: Přístup k objektům Interop sady Office pomocí funkcí Visual C#](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)|Ukazuje, jak vytvořit projekt, který používá pojmenovaných a nepovinných argumentů `dynamic` typ a další rozšíření, které zjednodušují přístup k rozhraní API Office objekty.|
