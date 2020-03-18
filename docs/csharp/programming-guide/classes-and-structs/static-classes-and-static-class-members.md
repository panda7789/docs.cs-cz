---
title: Statické třídy a statické členy třídy - Průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, static members
- static members [C#]
- static classes [C#]
- C# language, static classes
- static class members [C#]
ms.assetid: 235614b5-1371-4dbd-9abd-b406a8b0298b
ms.openlocfilehash: 7add512b262afbabe996f752c083566a2c394dfd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705428"
---
# <a name="static-classes-and-static-class-members-c-programming-guide"></a>Statické třídy a jejich členové (Průvodce programováním v C#)

[Statická](../../language-reference/keywords/static.md) třída je v podstatě stejná jako nestatická třída, ale existuje jeden rozdíl: statickou třídu nelze vytvořit instanci. Jinými slovy nelze použít [nový](../../language-reference/operators/new-operator.md) operátor k vytvoření proměnné typu třídy. Vzhledem k tomu, že neexistuje žádná proměnná instance, získáte přístup k členům statické třídy pomocí samotného názvu třídy. Například pokud máte statickou třídu, která je pojmenována, `UtilityClass` která má veřejnou statickou metodu s názvem `MethodA`, zavoláte metodu, jak je znázorněno v následujícím příkladu:  
  
```csharp  
UtilityClass.MethodA();  
```  
  
 Statickou třídu lze použít jako vhodný kontejner pro sady metod, které pracují pouze na vstupních parametrech a nemusí získat nebo nastavit žádná pole vnitřní instance. Například v knihovně tříd rozhraní .NET Framework obsahuje statická <xref:System.Math?displayProperty=nameWithType> třída metody, které provádějí matematické operace, bez <xref:System.Math> požadavku na uložení nebo načtení dat, která jsou jedinečná pro konkrétní instanci třídy. To znamená, že členy třídy použijete zadáním názvu třídy a názvu metody, jak je znázorněno v následujícím příkladu.  
  
```csharp  
double dub = -3.14;  
Console.WriteLine(Math.Abs(dub));  
Console.WriteLine(Math.Floor(dub));  
Console.WriteLine(Math.Round(Math.Abs(dub)));  
  
// Output:  
// 3.14  
// -4  
// 3  
```  
  
 Stejně jako u všech typů tříd, informace o typu pro statickou třídu jsou načteny zaběhem CLR (COMMON Language Runtime) rozhraní .NET Framework, který odkazuje na třídu. Program nemůže přesně určit, kdy je třída načtena. Je však zaručeno, že bude načtena a jeho pole inicializována a jeho statický konstruktor volán před tím, než je třída poprvé odkazována v programu. Statický konstruktor se nazývá pouze jednou a statická třída zůstane v paměti po dobu životnosti domény aplikace, ve které je program umístěn.  
  
> [!NOTE]
> Chcete-li vytvořit nestatickou třídu, která umožňuje vytvořit pouze jednu samotnou instanci, naleznete [v tématu Implementace singletonu v c#](https://docs.microsoft.com/previous-versions/msp-n-p/ff650316%28v=pandp.10%29).  
  
 Následující seznam obsahuje hlavní rysy statické třídy:  
  
- Obsahuje pouze statické členy.  
  
- Nelze vytvořit instanci.  
  
- Je zapečetěný.  
  
- Nelze obsahovat [konstruktory instance](./instance-constructors.md).  
  
 Vytvoření statické třídy je tedy v podstatě stejné jako vytvoření třídy, která obsahuje pouze statické členy a soukromý konstruktor. Soukromý konstruktor zabraňuje vytvoření instance třídy. Výhodou použití statické třídy je, že kompilátor může zkontrolovat, zda nejsou omylem přidány žádné členy instance. Kompilátor zaručí, že instance této třídy nelze vytvořit.  
  
 Statické třídy jsou zapečetěny a proto nelze zdědit. Nemohou dědit z <xref:System.Object>žádné třídy s výjimkou . Statické třídy nemohou obsahovat konstruktor instance; však mohou obsahovat statický konstruktor. Nestatické třídy by měly také definovat statický konstruktor, pokud třída obsahuje statické členy, které vyžadují netriviální inicializaci. Další informace naleznete [v tématu Statické konstruktory](./static-constructors.md).  
  
## <a name="example"></a>Příklad  
 Zde je příklad statické třídy, která obsahuje dvě metody, které převádějí teplotu z Celsia na Fahrenheita a z Fahrenheita na Celsia:  
  
 [!code-csharp[csProgGuideObjects#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#31)]  
  
## <a name="static-members"></a>Statické členy  
 Nestatická třída může obsahovat statické metody, pole, vlastnosti nebo události. Statický člen je volatelný ve třídě i v případě, že nebyla vytvořena žádná instance třídy. Statický člen je vždy přístupný podle názvu třídy, nikoli podle názvu instance. Existuje pouze jedna kopie statického člena, bez ohledu na to, kolik instancí třídy je vytvořeno. Statické metody a vlastnosti nemají přístup k nestatickým polím a událostem v jejich obsahujícím typu a nemohou získat přístup k proměnné instance libovolného objektu, pokud nejsou explicitně předány v parametru metody.  
  
 Je typičtější deklarovat nestatickou třídu s některými statickými členy, než deklarovat celou třídu jako statickou. Dvě běžná použití statických polí jsou zachovat počet objektů, které byly vytvořena instance, nebo uložit hodnotu, která musí být sdílena mezi všechny instance.  
  
 Statické metody mohou být přetíženy, ale nejsou přepsány, protože patří do třídy a nikoli do žádné instance třídy.  
  
 Přestože pole nelze `static const`deklarovat jako , [const](../../language-reference/keywords/const.md) pole je v podstatě statické ve svém chování. Patří k typu, nikoli k instancím typu. Proto const pole lze přistupovat pomocí `ClassName.MemberName` stejného zápisu, který se používá pro statická pole. Není vyžadována žádná instance objektu.  
  
 C# nepodporuje statické místní proměnné (proměnné, které jsou deklarovány v oboru metody).  
  
 Deklarujete statické `static` členy třídy pomocí klíčového slova před návratový typ člena, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideObjects#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#29)]  
  
 Statické členy jsou inicializovány před statickou člen je přístupný poprvé a před statický konstruktor, pokud existuje, je volána. Chcete-li získat přístup k statickému členu třídy, použijte název třídy namísto názvu proměnné k určení umístění člena, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideObjects#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#30)]  
  
 Pokud vaše třída obsahuje statická pole, zadejte statický konstruktor, který je inicializuje při načtení třídy.  
  
 Volání statické metody generuje instrukce volání v zprostředkujícím jazyce Microsoft (MSIL), zatímco `callvirt` volání metody instance generuje instrukce, která také kontroluje odkazy na nulový objekt. Většina času však rozdíl výkonu mezi těmito dvěma není významný.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  

Další informace naleznete [v tématu Statické třídy](~/_csharplang/spec/classes.md#static-classes) a [statické a členy instance](~/_csharplang/spec/classes.md#static-and-instance-members) ve [specifikaci jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Statické](../../language-reference/keywords/static.md)
- [Třídy](./classes.md)
- [Třída](../../language-reference/keywords/class.md)
- [Statické konstruktory](./static-constructors.md)
- [Konstruktory instancí](./instance-constructors.md)
