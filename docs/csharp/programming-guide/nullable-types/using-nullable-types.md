---
title: "Použití typů s povolenou hodnotou Null (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c8a42392bbcd2e53c54ff4c13bf98c048262ae4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-nullable-types-c-programming-guide"></a>Použití typů s povolenou hodnotou Null (Průvodce programováním v C#)
Typy s možnou hodnotou Null může představovat všechny hodnoty základní typ a další [null](../../../csharp/language-reference/keywords/null.md) hodnotu. Typy s možnou hodnotou Null jsou deklarované v jednom ze dvou způsobů:  
  
 `System.Nullable<T> variable`  
  
 -nebo-  
  
 `T? variable`  
  
 `T`je základní typ typ s možnou hodnotou Null. `T`může být libovolný typ hodnoty včetně `struct`; nemůže být odkazového typu.  
  
 Příklad může při použití typu s povolenou hodnotou Null, zvažte, jak obyčejnou Logická proměnná může mít dvě hodnoty: true a false. Neexistuje žádná hodnota, která označuje, že "undefined". V mnoha aplikacích programování zejména databáze interakce, proměnné se může objevit v nedefinované stavu. Například na pole v databázi mohou obsahovat hodnoty true nebo false, ale žádná hodnota může obsahovat také vůbec. Podobně odkazové typy může být nastaven na `null` indikující, že nejsou inicializovány.  
  
 Tento rozdíl lze vytvořit velmi programovací pracovní s další proměnné, které se používají k ukládání informací o stavu, použití speciální hodnoty a tak dále. Typ s možnou hodnotou Null modifikátor umožňuje C# k vytvoření typu hodnoty proměnné, které označují nedefinovanou hodnotu.  
  
## <a name="examples-of-nullable-types"></a>Příklady typů s povolenou hodnotou Null  
 Libovolný typ hodnoty slouží jako základ pro typ s možnou hodnotou Null. Příklad:  
  
 [!code-csharp[csProgGuideTypes#4](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_1.cs)]  
  
## <a name="the-members-of-nullable-types"></a>Členové typy s možnou hodnotou Null  
 Každá instance typu s povolenou hodnotou Null má dvě veřejné vlastnosti jen pro čtení:  
  
-   `HasValue`  
  
     `HasValue`je typu `bool`. Je nastaven na hodnotu `true` Pokud proměnná obsahuje hodnotu než null.  
  
-   `Value`  
  
     `Value`je stejného typu jako nadřazený typ. Pokud `HasValue` je `true`, `Value` obsahuje hodnotu smysluplný. Pokud `HasValue` je `false`, přístupu k `Value` vyvolá výjimku <xref:System.InvalidOperationException>.  
  
 V tomto příkladu `HasValue` člen se používá k ověření, zda proměnná obsahuje hodnotu, než se pokusí ji zobrazit.  
  
 [!code-csharp[csProgGuideTypes#5](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_2.cs)]  
  
 Testování pro hodnotu lze také provést jako v následujícím příkladu:  
  
 [!code-csharp[csProgGuideTypes#6](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_3.cs)]  
  
## <a name="explicit-conversions"></a>Explicitní převody  
 Typ s možnou hodnotou Null lze převést na typu regulární explicitně s přetypování nebo pomocí `Value` vlastnost. Příklad:  
  
 [!code-csharp[csProgGuideTypes#7](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_4.cs)]  
  
 Pokud definovaná uživatelem definovaný převod mezi dvěma datovými typy, stejné převod mohou sloužit také s možnou hodnotou Null verze těchto datových typů.  
  
## <a name="implicit-conversions"></a>Implicitní převody  
 Proměnná typu s povolenou hodnotou Null lze nastavit na hodnotu null s `null` – klíčové slovo, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideTypes#8](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_5.cs)]  
  
 Je implicitní převod z typu obyčejnou na typ s možnou hodnotou Null.  
  
 [!code-csharp[csProgGuideTypes#9](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_6.cs)]  
  
## <a name="operators"></a>Operátory  
 Předdefinované Unární a binární operátory a uživatelem definované operátory, které existují u typů hodnot může také použít pro typy s možnou hodnotou Null. Tyto operátory vytvořit hodnotu null, pokud operandy jsou null. operátor, jinak používá obsažené hodnotu vypočítat výsledek. Příklad:  
  
 [!code-csharp[csProgGuideTypes#10](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_7.cs)]  
  
 Při provádění porovnávání s typy s možnou hodnotou Null, pokud jeden z typů s povolenou hodnotou Null hodnotu null a dalších není všechny porovnání vyhodnocení `false` s výjimkou `!=` (nerovná). Je důležité, abyste předpokládat, že vzhledem k tomu, že konkrétní porovnání vrátí `false`, opačném případě vrátí `true`. V následujícím příkladu 10 není větší než je menší než ani rovnat na hodnotu null. Pouze `num1 != num2` vyhodnocuje `true`.  
  
 [!code-csharp[csProgGuideTypes#11](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_8.cs)]  
  
 Porovnání rovnosti dva typy s možnou hodnotou Null, které jsou oba hodnotu null se vyhodnocuje `true`.  
  
## <a name="the--operator"></a>Na?? Operátor  
 `??` Operátor definuje výchozí hodnotu, která je vrácena, pokud typ s možnou hodnotou Null se přiřadí k použití hodnot Null typu.  
  
 [!code-csharp[csProgGuideTypes#12](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_9.cs)]  
  
 Tento operátor. můžete také použít s více typy s možnou hodnotou Null. Příklad:  
  
 [!code-csharp[csProgGuideTypes#13](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_10.cs)]  
  
## <a name="the-bool-type"></a>Bool? Typ  
 `bool?` Typ s možnou hodnotou Null může obsahovat tři různé hodnoty: [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md) a [null](../../../csharp/language-reference/keywords/null.md). Informace o tom, jak převést z bool? bool, najdete v tématu [postupy: bezpečné přetypování z bool? na bool](../../../csharp/programming-guide/nullable-types/how-to-safely-cast-from-bool-to-bool.md).  
  
 S možnou hodnotou Null logické hodnoty jsou stejné jako logická hodnota proměnné typ, který se používá v systému SQL. Zajistit, aby výsledky vyprodukované `&` a `|` operátory jsou konzistentní s typem Boolean s hodnotou tři v SQL, jsou k dispozici následující předdefinované operátory:  
  
 `bool? operator &(bool? x, bool? y)`  
  
 `bool? operator |(bool? x, bool? y)`  
  
 Výsledky těchto operátorů jsou uvedené v následující tabulce:  
  
|X|y|x a y|x &#124; y|  
|-------|-------|---------|--------------|  
|true|true|true|true|  
|true|false|false|true|  
|true|null|null|true|  
|false|true|false|true|  
|false|false|false|false|  
|false|null|false|null|  
|null|true|null|true|  
|null|false|false|null|  
|null|null|null|null|  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Typy s možnou hodnotou Null](../../../csharp/programming-guide/nullable-types/index.md)  
 [Zabalení typů s povolenou hodnotou Null](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)  
 [Typy hodnot s povolenou hodnotou Null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
