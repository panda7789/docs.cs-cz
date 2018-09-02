---
title: Statické třídy a jejich členové (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, static members
- static members [C#]
- static classes [C#]
- C# language, static classes
- static class members [C#]
ms.assetid: 235614b5-1371-4dbd-9abd-b406a8b0298b
ms.openlocfilehash: f3e64d975d2845d8317b37f43c3811af6be03b55
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43468694"
---
# <a name="static-classes-and-static-class-members-c-programming-guide"></a>Statické třídy a jejich členové (Průvodce programováním v C#)
A [statické](../../../csharp/language-reference/keywords/static.md) třída je v podstatě stejný jako nestatické třídy, ale je jedním z rozdílů: Nelze vytvořit instanci statické třídy. Jinými slovy, nelze použít [nové](../../../csharp/language-reference/keywords/new.md) – klíčové slovo vytvoření proměnné typu třídy. Protože neexistuje žádná instance proměnné, přístup jako objekty její členové statické třídy pomocí samotný název třídy. Například, pokud mají statickou třídu, která se jmenuje `UtilityClass` , který má veřejnou metodu s názvem `MethodA`, zavolejte metodu, jak je znázorněno v následujícím příkladu:  
  
```csharp  
UtilityClass.MethodA();  
```  
  
 Statická třída může sloužit jako praktický kontejner pro sadu metod, které právě zpracovat vstupní parametry a nemají k získání nebo nastavení jakékoli instanci interní pole. Například v knihovně tříd rozhraní .NET Framework, statické <xref:System.Math?displayProperty=nameWithType> třída obsahuje metody, které provádějí matematické operace, aniž by byl ukládat nebo načítat data, která jsou jedinečné pro konkrétní instanci <xref:System.Math> třídy. To znamená, že použijete členy třídy tak, že zadáte název třídy a název metody, jak je znázorněno v následujícím příkladu.  
  
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
  
 Jak je tomu u všech typů tříd, informace o typu pro statické třídy načítá [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] common language runtime (CLR) při načtení programu, který odkazuje na třídu. Program nelze zadat přesně při načtení třídy. Ale je zaručeno, že má být načten a inicializován polí a jeho statický konstruktor voláno před provedením třídy odkazuje ve svém programu poprvé. Statický konstruktor je volat pouze jednou a statická třída zůstanou v paměti dobu životnosti domény aplikace, ve kterém se nachází váš program.  
  
> [!NOTE]
>  Chcete-li vytvořit nestatické třídy, která umožňuje pouze jednu instanci sebe sama, který se má vytvořit, naleznete v tématu [implementace jednotlivý prvek v jazyce C#](https://msdn.microsoft.com/library/ms998558.aspx).  
  
 Následující seznam obsahuje hlavní funkce statické třídy:  
  
-   Obsahuje pouze statické členy.  
  
-   Nelze vytvořit instanci.  
  
-   Je zapečetěná.  
  
-   Nesmí obsahovat [konstruktory instancí](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  
  
 Vytvoření statické třídy je tedy v podstatě stejné jako vytvoření třídy, která obsahuje pouze statické členy a soukromý konstruktor. Soukromý konstruktor zabraňuje instance třídy. Výhodou použití statické třídy je, že kompilátor můžete zkontrolovat, nezapomeňte omylem přidat žádné členy instance. Kompilátor zaručí, že nelze vytvořit instance této třídy.  
  
 Statické třídy jsou zapečetěné a proto nemůže být zděděna. Nemůže dědit z jiné třídy, s výjimkou <xref:System.Object>. Statické třídy nemůžou obsahovat konstruktor instance; však mohou obsahovat statický konstruktor. Třídy nestatických by mělo definovat i statického konstruktoru, pokud třída obsahuje statické členy, které vyžadují netriviální inicializace. Další informace najdete v tématu [statické konstruktory](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
## <a name="example"></a>Příklad  
 Tady je příklad, který obsahuje dvě metody, které převést teplotu ve stupních Celsia na stupně Fahrenheita a Fahrenheita na stupně Celsia statické třídy:  
  
 [!code-csharp[csProgGuideObjects#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-classes-and-static-class-members_1.cs)]  
  
## <a name="static-members"></a>Statické členy  
 Nestatické třídy mohou obsahovat statické metody, pole, vlastnosti nebo události. Statický člen je volatelná třídy i v případě, že byla vytvořena žádná instance třídy. Statický člen se vždy přistupuje pomocí názvu třídy, nikoli název instance. Jenom jednu kopii statického člena, který existuje, bez ohledu na to, kolik instancí třídy jsou vytvořeny. Statické metody a vlastnosti nemůže přistupovat k nestatickému pole a události v jejich nadřazeným typem a nemají přístup k proměnné instance objektu, pokud je explicitně předán v parametru metody.  
  
 Je obvyklejší deklarujte nestatické třídy se některé statické členy, než Chcete-li deklarovat celou třídu jako statické. Dvě běžné použití statických polí jsou udržovat přehled o počtu počet objektů, které byly vytvořeny nebo uložit hodnotu, která musí být sdílená mezi všemi instancemi.  
  
 Statické metody může být přetížena ale nebyly přepsány, protože náleží do třídy a ne na jakoukoli instanci třídy.  
  
 I když pole nemůže být deklarována jako `static const`, [const](../../../csharp/language-reference/keywords/const.md) pole je v podstatě statické, jeho chování. Patří k typu, nikoli do instance daného typu. Proto argument pole je přístupná pomocí stejného `ClassName.MemberName` zápis, který se používá pro statické pole. Žádná instance objektu je povinný.  
  
 C# nepodporuje statické lokální proměnné (proměnné, které jsou deklarovány v oboru metody).  
  
 Deklarace statické členy třídy pomocí `static` – klíčové slovo před návratovým typem člena, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideObjects#29](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-classes-and-static-class-members_2.cs)]  
  
 Statické členy jsou inicializovány statické členské se před přístupem k prvním a před statický konstruktor, pokud existuje, je volána. Pro přístup ke členu statické třídy, použijte název třídy místo názvu proměnné a určí tak umístění člena, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideObjects#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-classes-and-static-class-members_3.cs)]  
  
 Pokud vaše třída obsahuje statická pole, zadejte statický konstruktor, který inicializuje je při načtení třídy.  
  
 Volání statické metody generuje instrukcí volání v jazyce Microsoft intermediate language (MSIL), že volání metody instance generuje `callvirt` instrukce, což také kontroluje odkazuje na objekt s hodnotou null. Ale ve většině případů rozdíly ve výkonnosti mezi těmito dvěma není důležité.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [static](../../../csharp/language-reference/keywords/static.md)  
 [Třídy](../../../csharp/programming-guide/classes-and-structs/classes.md)  
 [class](../../../csharp/language-reference/keywords/class.md)  
 [Statické konstruktory](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)  
 [Konstruktory instancí](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)
