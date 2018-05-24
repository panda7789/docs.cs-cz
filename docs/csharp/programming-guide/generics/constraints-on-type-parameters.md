---
title: Omezení parametrů typů (Průvodce programováním v C#)
ms.date: 04/12/2018
helpviewer_keywords:
- generics [C#], type constraints
- type constraints [C#]
- type parameters [C#], constraints
- unbound type parameter [C#]
ms.openlocfilehash: b5ad639309238912aa27b58c95466b4f37052699
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2018
---
# <a name="constraints-on-type-parameters-c-programming-guide"></a>Omezení parametrů typů (C# Průvodce programováním)

Omezení kompilátoru informovat o funkcích, které musí mít argument typu. Bez žádná omezení může být argument typu libovolného typu. Kompilátor můžete předpokládat pouze členové <xref:System.Object?displayPropety=nameWithType>, což je ultimate základní třídu pro jakýkoli typ rozhraní .NET. Další informace najdete v tématu [Proč používat omezení](#why-use-constraints). Pokud kód klienta se pokusí vytvořit třídu pomocí typu, která není povolena omezení, výsledkem je chyba kompilace. Omezení zadávají pomocí `where` kontextové klíčové slovo. Následující tabulka uvádí typy sedm omezení:

|Omezení|Popis|
|----------------|-----------------|
|`where T : struct`|Argument typu musí být typ hodnoty. Některé hodnoty typ s výjimkou <xref:System.Nullable> lze zadat. Další informace najdete v tématu [pomocí typy s možnou hodnotou Null](../nullable-types/using-nullable-types.md).|
|`where T : class`|Argument typu musí být odkazového typu. Toto omezení platí také pro třídu, rozhraní, delegát nebo typ pole.|
|`where T : unmanaged`|Argument typu nesmí být odkazového typu a nesmí obsahovat žádné členy typu odkaz na libovolnou úroveň vnoření.|
|`where T : new()`|Argument typu musí mít konstruktor public bez parametrů. Při použití spolu s jiná omezení `new()` omezení musí být uvedený jako poslední.|
|`where T :` *\<Název základní třídy >*|Argument typu musí být nebo odvozena od zadané základní třídy.|
|`where T :` *\<Název rozhraní >*|Argument typu musí být nebo implementovat rozhraní zadaný. Je možné zadat více omezení rozhraní. Omezení rozhraní může být také obecné.|
|`where T : U`|Argument typu zadaná pro T musí být nebo odvozena od argument zadaný pro U.|

Některá omezení se vzájemně vylučují. Všechny typy hodnot musí mít přístupné bezparametrový konstruktor. `struct` Znamená omezení `new()` omezení a `new()` omezení nelze kombinovat s `struct` omezení. `unmanaged` Znamená omezení `struct` omezení. `unmanaged` Omezení nelze kombinovat s buď `struct` nebo `new()` omezení.

## <a name="why-use-constraints"></a>Proč používat omezení

Omezíte parametr typu, můžete zvýšit počet povolených operací a volání metody jsou podporovány všechny typy v hierarchii dědičnosti a omezení typu. Při návrhu obecné třídy nebo metody, pokud se budete provádět všechny operace v obecné členy nad rámec jednoduché přiřazení nebo volání žádné metody, které nepodporují <xref:System.Object?displayProperty=nameWithType>, budete muset použít omezení pro parametr typu. Například omezení základní třídy říká kompilátoru, že pouze objekty tohoto typu nebo odvozené z tohoto typu se použije jako argumenty typu. Jakmile kompilátor tento záruka, můžete povolit metod k volání ve třídě obecného typu. Následující příklad kódu ukazuje funkci můžete přidat do `GenericList<T>` – třída (v [Úvod do obecných typů](introduction-to-generics.md)) použitím omezení základní třídy.

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#9)]

Omezení umožňuje obecná třída používat `Employee.Name` vlastnost. Omezení určuje, že všechny položky typu `T` jsou musí být buď `Employee` objekt nebo objekt, který dědí z `Employee`.

Více omezení lze použít pro stejný parametr typu a omezení sami lze obecné typy, následujícím způsobem:

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#10)]

Při použití `where T : class` omezení, vyhněte se `==` a `!=` operátory na parametr typu vzhledem k tomu, že tyto operátory testovat pro referenční identity jenom, ne pro rovnosti hodnoty. K tomuto chování dochází, i když jsou tyto operátory přetížené v typu, který se používá jako argument. Následující kód ukazuje tento bod; i když je hodnota false výstup <xref:System.String> třídy přetížení `==` operátor.

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#11)]

Kompilátor pouze ví, že T typem je odkaz v době kompilace a musí používat výchozí operátory, které jsou platné pro všechny typy odkazů. Pokud musíte otestovat rovnosti hodnotu, doporučený způsob je se rovněž vztahují `where T : IEquatable<T>` nebo `where T : IComparable<T>` omezení a implementace rozhraní do třídy, která se použije ke konstrukci obecná třída.

## <a name="constraining-multiple-parameters"></a>Chovaly několik parametrů

Omezení můžete použít pro několik parametrů a více omezení pro jeden parametr, jak je znázorněno v následujícím příkladu:

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#12)]

## <a name="unbounded-type-parameters"></a>Parametry typu bez vazby

 Zadejte parametry, které mají žádná omezení, jako je například T v veřejnou třídu `SampleClass<T>{}`, se nazývají typu bez vazby parametrů. Parametry typu bez vazby mají následující pravidla:

- `!=` a `==` operátory nelze použít, protože není zaručeno, že konkrétní typ argumentu bude podporovat tyto operátory.
- Mohou být převedeny do a z `System.Object` nebo explicitně převést na typ všech rozhraní.
- Můžete porovnat jejich [null](../../language-reference/keywords/null.md). Pokud se porovná bez vazby parametru `null`, porovnání vždy vrátí hodnotu false, pokud argument typ je typ hodnoty.

## <a name="type-parameters-as-constraints"></a>Parametry typu jako omezení

Použití parametr obecného typu jako omezení je užitečné, pokud členské funkce s parametrem vlastní typ má omezit tento parametr pro parametr typu obsahující typu, jak je znázorněno v následujícím příkladu:

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#13)]

V předchozím příkladu `T` je omezení typu v kontextu `Add` metoda a parametru typu bez vazby v kontextu `List` třídy.

Parametry typu mohou sloužit také jako omezení v definicích – obecná třída. Parametr typu musí být deklarován v závorkách úhel spolu s dalšími parametry typu:

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#14)]

Užitečnost parametry typu jako omezení s obecné třídy je omezená, protože kompilátor můžete předpokládat nic o parametr typu s tím rozdílem, že je odvozena z `System.Object`. Pomocí parametrů typu jako omezení obecných tříd ve scénářích, ve kterých chcete vynutit vztah dědičnosti mezi dvěma parametry typu.

## <a name="unmanaged-constraint"></a>Nespravované omezení

Počínaje 7.3 C#, můžete použít `unmanaged` omezení k určení, že musí být parametr typu **nespravované typu**. **Nespravované typu** je typ, který není typu odkazu a neobsahuje pole typu odkaz na libovolnou úroveň vnoření. `unmanaged` Omezení umožňuje zapisovat opakovaně použitelné rutiny pro práci s typy, které smí uživatel manipulovat jako bloky paměti, jak je znázorněno v následujícím příkladu:

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#15)]

Předchozí postup musí být zkompilovány v `unsafe` kontextu protože používá `sizeof` operátor pro typ není známý jako předdefinovaný typ. Bez `unmanaged` omezení, `sizeof` operátor je k dispozici.

## <a name="delegate-constraints"></a>Delegát omezení

Také počínaje 7.3 C#, můžete použít <xref:System.Delegate?displayProperty=nameWithType> nebo <xref:System.MulticastDelegate?displayProperty=nameWithType> jako základní třída omezení. Modul CLR vždycky povolená toto omezení, ale jazyka C# nepovolené ho. `System.Delegate` Omezení umožňuje psát kód, který funguje s delegáti způsobem bezpečnost typů. Následující kód definuje metody rozšíření, které se kombinuje dvě delegáti předpokladu, že jsou stejného typu:

[!code-csharp[using the delegate constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#16)]

Metodu výše můžete kombinování delegátů, které jsou stejného typu:

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#17)]

Pokud zrušte komentář u poslední řádek nebude zkompilují. Obě `first` a `test` jsou typy delegáta, ale jsou typy různých delegáta.

## <a name="enum-constraints"></a>Omezení výčtu

Počínaje 7.3 C#, můžete také určit <xref:System.Enum?displayProperty=nameWithType> typ jako základní třída omezení. Modul CLR vždycky povolená toto omezení, ale jazyka C# nepovolené ho. Obecné typy pomocí `System.Enum` poskytují bezpečnost typů programování výsledky do mezipaměti pomocí statických metod v `System.Enum`. Následující příklad vyhledá všechny platné hodnoty pro typ výčtu a potom vytvoří slovník, který mapuje tyto hodnoty na řetězcovou reprezentaci.

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#18)]

Ujistěte se, metody použité pomocí reflexe, který má ovlivnit výkon. Můžete volat tuto metodu za účelem vytvoření kolekce, která je do mezipaměti a znovu použít místo opakování volání, které vyžadují reflexe.

Je možné jej použít jak znázorňuje následující ukázka vytvořit výčet a sestavení slovník jeho hodnoty a názvy:

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#19)]

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#20)]

## <a name="see-also"></a>Viz také

 <xref:System.Collections.Generic> [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Úvod do obecných typů](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [Obecné třídy](../../../csharp/programming-guide/generics/generic-classes.md)  
 [new – omezení](../../../csharp/language-reference/keywords/new-constraint.md)  
