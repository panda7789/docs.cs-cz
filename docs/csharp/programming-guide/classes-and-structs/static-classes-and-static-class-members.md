---
title: "Statické třídy a jejich členové (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, static members
- static members [C#]
- static classes [C#]
- C# language, static classes
- static class members [C#]
ms.assetid: 235614b5-1371-4dbd-9abd-b406a8b0298b
caps.latest.revision: "49"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cf2517dd5989d36341b840ffcb476cbeb14baf54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="static-classes-and-static-class-members-c-programming-guide"></a>Statické třídy a jejich členové (Průvodce programováním v C#)
A [statické](../../../csharp/language-reference/keywords/static.md) třída je v podstatě stejný jako nestatickou třídu, ale je jeden rozdíl: statická třída nelze vytvořit instanci. Jinými slovy, nemůžete použít [nové](../../../csharp/language-reference/keywords/new.md) – klíčové slovo vytvoření proměnné typu třídy. Protože neexistuje žádná instance proměnné, máte přístup k členové statické třídy pomocí samotný název třídy. Například pokud máte statického třídy, která má název `UtilityClass` s veřejnou metodu s názvem `MethodA`, volejte metodu, jak je znázorněno v následujícím příkladu:  
  
```csharp  
UtilityClass.MethodA();  
```  
  
 Statická třída slouží jako kontejner vhodné pro sady metod, které právě pracují vstupní parametry a nemají k získání nebo nastavení všechna pole interní instance. Například v knihovně tříd rozhraní .NET Framework, statické <xref:System.Math?displayProperty=nameWithType> třída obsahuje metody, které provádějí matematické operace, aniž by bylo nutné ukládat a načítat data, která jsou jedinečná pro konkrétní instanci <xref:System.Math> třídy. To znamená můžete použít členy třídy tak, že zadáte název třídy a název metody, jak je znázorněno v následujícím příkladu.  
  
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
  
 Je tomu u všechny typy tříd, informací o typu pro statická třída zavedená [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] modul common language runtime (CLR), když je načten program, který odkazuje na třídu. Program nelze zadat přesně při načtení třídy. Nicméně je zaručeno, má být načten a na jeho pole inicializovat a jeho statického konstruktoru voláno před provedením třída odkazuje poprvé v programu. Statický konstruktor je volána pouze jednou a statická třída zůstane v paměti pro dobu životnosti domény aplikace, ve kterém se nachází váš program.  
  
> [!NOTE]
>  Vytvoření nestatickou třídu, která povoluje pouze jednu instanci vlastní kód, který se má vytvořit, naleznete v části [implementace jednotlivý prvek v C#](http://go.microsoft.com/fwlink/?LinkID=100567).  
  
 Následující seznam obsahuje hlavní funkce statické třídy:  
  
-   Obsahuje pouze statické členy.  
  
-   Nelze vytvořit instanci.  
  
-   Je zapečetěná.  
  
-   Nemůže obsahovat [konstruktory instancí](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  
  
 Vytvoření statické třídy je tedy v podstatě stejný jako vytváření třídu, která obsahuje jenom statické členy a soukromý konstruktor. Soukromý konstruktor zabrání vytváření instancí třídy. Výhodou použití statická třída je, že kompilátor můžete zkontrolovat a ujistěte se, že žádné členy instancí jsou omylem přidán. Kompilátor zaručí, že instance této třídy nelze vytvořit.  
  
 Statické třídy jsou zapečetěné a nelze ji proto zdědit. Nelze zdědit z libovolné třídy s výjimkou <xref:System.Object>. Statické třídy nemohou obsahovat konstruktoru instance; však mohou obsahovat statický konstruktor. Nestatické třídy měli také definovat statického konstruktoru, pokud třída obsahuje statické členy, které vyžadují netriviální inicializace. Další informace najdete v tématu [statické konstruktory](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
## <a name="example"></a>Příklad  
 Tady je příklad statické třídy, která obsahuje dvě metody, které převést teploty z c na Fahrenheita a Fahrenheita k c:  
  
 [!code-csharp[csProgGuideObjects#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-classes-and-static-class-members_1.cs)]  
  
## <a name="static-members"></a>Statické členy  
 Nestatické třídy může obsahovat statických metod, polí, vlastnosti a události. Statický člen je možné volat na třídě, i když se vytvořil žádná instance třídy. Statický člen vždy přístup k názvu třídy, ne název instance. Existuje pouze jedna kopie je statický člen, bez ohledu na to, kolik instancí třídy jsou vytvořeny. Statické metody a vlastnosti nemůže získat přístup nestatické pole a události v jejich obsahující typ, a pokud je výslovně předán v parametru metody nemají přístup k proměnné instance libovolného objektu.  
  
 Je typičtější deklarovat nestatickou třídu s některé statických členů, než se deklarovat celou třídu jako statické. Dva běžná použití statických polí jsou si nechat počet objektů, které byly vytvořeny, nebo uložit hodnotu, která musí být sdílen všechny instance.  
  
 Statické metody můžete přetížený ale přepsána nejsou, protože náleží do třídy a ne na jakoukoli instanci třídy.  
  
 I když pole nelze deklarovat jako `static const`, [const](../../../csharp/language-reference/keywords/const.md) pole je v podstatě statické ve své chování. Patří do typu, aby instance typu. Proto const pole je přístupná pomocí stejné `ClassName.MemberName` zápis, který se používá pro statických polí. Vyžaduje se žádná instance objektu.  
  
 C# nepodporuje statické místní proměnné (proměnné, které jsou deklarované v oboru metoda).  
  
 Deklarace členové statické třídy pomocí `static` – klíčové slovo před návratový typ člena, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideObjects#29](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-classes-and-static-class-members_2.cs)]  
  
 Statické členy se inicializují před statický člen přistupuje poprvé a před statického konstruktoru, pokud existuje, je volána. O přístup člena statická třída, použijte název třídy místo název proměnné a určete tak umístění člena, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideObjects#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-classes-and-static-class-members_3.cs)]  
  
 Pokud vaše třída obsahuje statická pole, zadejte statický konstruktor, který inicializuje je při načítání třídy.  
  
 Volání statickou metodu generuje volání instrukce v Microsoft (MSIL intermediate language), zatímco generuje volání metody instance `callvirt` instrukce, které také zkontroluje pro odkazuje na objekt s hodnotou null. Ale ve většině případů výkonu rozdíl mezi nimi není důležité.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [statické](../../../csharp/language-reference/keywords/static.md)  
 [Třídy](../../../csharp/programming-guide/classes-and-structs/classes.md)  
 [– Třída](../../../csharp/language-reference/keywords/class.md)  
 [Statické konstruktory](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)  
 [Konstruktory instancí](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)
