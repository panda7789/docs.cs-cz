---
title: "Omezení parametrů typů (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], type constraints
- type constraints [C#]
- type parameters [C#], constraints
- unbound type parameter [C#]
ms.assetid: 141b003e-1ddb-4e1c-bcb2-e1c3870e6a51
caps.latest.revision: "41"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6f7c80acdb3815af4b5d545297894778029a9104
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/20/2018
---
# <a name="constraints-on-type-parameters-c-programming-guide"></a>Omezení parametrů typů (Průvodce programováním v C#)
Při definování obecné třídy, můžete použít omezení na typy typy, které kód klienta můžete použít pro argumenty typu při třídě. Pokud kód klienta se pokusí vytvořit třídu pomocí typu, která není povolena omezení, výsledkem je chyba kompilace. Tato omezení se nazývají omezení. Omezení zadávají pomocí `where` kontextové klíčové slovo. Následující tabulka uvádí šest typy omezení:  
  
|Omezení|Popis|  
|----------------|-----------------|  
|`where T: struct`|Argument typu musí být typ hodnoty. Některé hodnoty typ s výjimkou <xref:System.Nullable> lze zadat. V tématu [pomocí typy s možnou hodnotou Null](../../../csharp/programming-guide/nullable-types/using-nullable-types.md) Další informace.|  
|`where T : class`|Argument typu musí být odkazového typu; To platí také pro třídu, rozhraní, delegát nebo typ pole.|  
|`where T : new()`|Argument typu musí mít konstruktor public bez parametrů. Při použití spolu s jiná omezení `new()` omezení musí být uvedený jako poslední.|  
|`where T : `*\<Název základní třídy >*|Argument typu musí být nebo odvozena od zadané základní třídy.|  
|`where T : `*\<Název rozhraní >*|Argument typu musí být nebo implementovat rozhraní zadaný. Je možné zadat více omezení rozhraní. Omezení rozhraní může být také obecné.|  
|`where T : U`|Argument typu zadaná pro T musí být nebo odvozena od argument zadaný pro U.|  
  
## <a name="why-use-constraints"></a>Proč používat omezení  
 Pokud chcete prozkoumat položky v seznamu obecné k určení, zda je platný a porovnejte je s některé jiné položky, musí mít kompilátor, některé zaručit, že operátor nebo metody, kterou musí volání bude podporovat některý argument typ, který může být určena co klienta Německo. Tato záruka se získávají použitím jeden nebo více omezení na vaší definice – obecná třída. Například omezení základní třídy říká kompilátoru, že pouze objekty tohoto typu nebo odvozené z tohoto typu se použije jako argumenty typu. Jakmile kompilátor tento záruka, můžete povolit metod k volání ve třídě obecného typu. Omezení se aplikují pomocí kontextové klíčové slovo `where`. Následující příklad kódu ukazuje funkci můžete přidáme `GenericList<T>` – třída (v [Úvod do obecných typů](../../../csharp/programming-guide/generics/introduction-to-generics.md)) použitím omezení základní třídy.  
  
 [!code-csharp[csProgGuideGenerics#11](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_1.cs)]  
  
 Omezení umožňuje obecná třída používat `Employee.Name` vlastnost vzhledem k tomu, že je zaručeno, že všechny položky typu t. buď `Employee` objekt nebo objekt, který dědí z `Employee`.  
  
 Více omezení lze použít pro stejný parametr typu a omezení sami lze obecné typy, následujícím způsobem:  
  
 [!code-csharp[csProgGuideGenerics#12](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_2.cs)]  
  
 Omezíte parametr typu, můžete zvýšit počet povolených operací a volání metody jsou podporovány všechny typy v hierarchii dědičnosti a omezení typu. Proto při navrhování obecné třídy nebo metody, pokud se budete provádět všechny operace v obecné členy nad rámec jednoduché přiřazení nebo volání žádné metody, které nepodporují `System.Object`, budete muset použít omezení pro parametr typu.  
  
 Při použití `where T : class` omezení, vyhněte se `==` a `!=` operátory na parametr typu vzhledem k tomu, že tyto operátory testovat pro referenční identity jenom, ne pro rovnosti hodnoty. Toto je tento případ, i když jsou tyto operátory přetížené v typu, který se používá jako argument. Následující kód ukazuje tento bod; i když je hodnota false výstup <xref:System.String> třídy přetížení `==` operátor.  
  
 [!code-csharp[csProgGuideGenerics#13](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_3.cs)]  
  
 Důvod pro toto chování je, že v době kompilace kompilátor pouze ví, že T typem je odkaz a proto musíte použít výchozí operátory, které jsou platné pro všechny typy odkazů. Pokud musíte otestovat rovnosti hodnotu, doporučený způsob je se rovněž vztahují `where T : IComparable<T>` omezení a implementace, která rozhraní do třídy, která se použije ke konstrukci obecná třída.  
  
## <a name="constraining-multiple-parameters"></a>Chovaly několik parametrů  
 Omezení můžete použít pro několik parametrů a více omezení pro jeden parametr, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideGenerics#64](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_4.cs)]  
  
## <a name="unbounded-type-parameters"></a>Parametry typu bez vazby  
 Zadejte parametry, které mají žádná omezení, jako je například T v veřejnou třídu `SampleClass<T>{}`, se nazývají typu bez vazby parametrů. Parametry typu bez vazby mají následující pravidla:  
  
-   `!=` a `==` operátory nelze použít, protože není zaručeno, že konkrétní typ argumentu bude podporovat tyto operátory.  
  
-   Mohou být převedeny do a z `System.Object` nebo explicitně převést na typ všech rozhraní.  
  
-   Můžete porovnat s [null](../../../csharp/language-reference/keywords/null.md). Pokud se porovná bez vazby parametru `null`, porovnání vždy vrátí hodnotu false, pokud argument typ je typ hodnoty.  
  
## <a name="type-parameters-as-constraints"></a>Parametry typu jako omezení  
 Použití parametr obecného typu jako omezení je užitečné, pokud členské funkce s parametrem vlastní typ má omezit tento parametr pro parametr typu obsahující typu, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideGenerics#14](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_5.cs)]  
  
 V předchozím příkladu `T` je omezení typu v kontextu `Add` metoda a parametru typu bez vazby v kontextu `List` třídy.  
  
 Parametry typu mohou sloužit také jako omezení v definicích – obecná třída. Všimněte si, že parametr typu musí být deklarován v závorkách úhel spolu s dalšími parametry typu:  
  
 [!code-csharp[csProgGuideGenerics#15](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_6.cs)]  
  
 Užitečnost parametry typu jako omezení s obecné třídy jsou hodně omezené, protože kompilátor můžete předpokládat nic o parametr typu s tím rozdílem, že je odvozena z `System.Object`. Pomocí parametrů typu jako omezení obecných tříd ve scénářích, ve kterých chcete vynutit vztah dědičnosti mezi dvěma parametry typu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.Generic>  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Úvod do obecných typů](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [Obecné třídy](../../../csharp/programming-guide/generics/generic-classes.md)  
 [new – omezení](../../../csharp/language-reference/keywords/new-constraint.md)
