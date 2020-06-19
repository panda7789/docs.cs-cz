---
title: Statické třídy a členy statické třídy – Průvodce programováním v C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, static members
- static members [C#]
- static classes [C#]
- C# language, static classes
- static class members [C#]
ms.assetid: 235614b5-1371-4dbd-9abd-b406a8b0298b
ms.openlocfilehash: 71cbf8278b3a8092e93a8ae3d8be291540f16cc3
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990106"
---
# <a name="static-classes-and-static-class-members-c-programming-guide"></a>Statické třídy a jejich členové (Průvodce programováním v C#)

[Statická](../../language-reference/keywords/static.md) třída je v podstatě stejná jako nestatická třída, ale existuje jeden rozdíl: statickou třídu nelze vytvořit. Jinými slovy, operátor [New](../../language-reference/operators/new-operator.md) nelze použít k vytvoření proměnné typu třídy. Vzhledem k tomu, že není k dispozici žádná proměnná instance, získáte přístup ke členům statické třídy pomocí samotného názvu třídy. Například pokud máte statickou třídu s názvem `UtilityClass` , která má veřejnou statickou metodu s názvem `MethodA` , zavoláte metodu, jak je znázorněno v následujícím příkladu:  
  
```csharp  
UtilityClass.MethodA();  
```  
  
 Statickou třídu lze použít jako pohodlný kontejner pro sady metod, které fungují pouze na vstupních parametrech a nemusejí získávat ani nastavovat žádná interní pole instance. Například v knihovně tříd .NET statická <xref:System.Math?displayProperty=nameWithType> Třída obsahuje metody, které provádějí matematické operace bez nutnosti ukládat nebo načítat data, která jsou jedinečná pro konkrétní instanci <xref:System.Math> třídy. To znamená, že použijete členy třídy zadáním názvu třídy a názvu metody, jak je znázorněno v následujícím příkladu.  
  
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
  
 Stejně jako u všech typů tříd jsou informace o typu statické třídy načteny modulem runtime .NET, když je načten program, který odkazuje na třídu. Program nemůže přesně určovat, kdy je třída načtena. Je však zaručeno, že bude načteno a že jeho pole jsou inicializována a jeho statický konstruktor byl volán před tím, než je třída poprvé odkazována v programu. Statický konstruktor se volá jenom jednou a statická třída zůstane v paměti po dobu života domény aplikace, ve které se váš program nachází.  
  
> [!NOTE]
> Chcete-li vytvořit nestatickou třídu, která umožňuje vytvořit pouze jednu instanci sebe sama, viz téma [implementace typu Singleton v jazyce C#](https://docs.microsoft.com/previous-versions/msp-n-p/ff650316%28v=pandp.10%29).  
  
 Následující seznam poskytuje hlavní funkce statické třídy:  
  
- Obsahuje pouze statické členy.  
  
- Nelze vytvořit instanci.  
  
- Je zapečetěný.  
  
- Nemůže obsahovat [konstruktory instancí](./instance-constructors.md).  
  
 Vytvoření statické třídy je proto v podstatě stejné jako vytvoření třídy, která obsahuje pouze statické členy a soukromý konstruktor. Privátní konstruktor zabraňuje vytvoření instance třídy. Výhodou použití statické třídy je, že kompilátor může zkontrolovat, zda nejsou omylem přidány žádné členy instance. Kompilátor zajistí, že instance této třídy nelze vytvořit.  
  
 Statické třídy jsou zapečetěné, a proto je nelze zdědit. Nemůžou dědit z žádné třídy s výjimkou <xref:System.Object> . Statické třídy nemůžou obsahovat konstruktor instance. Mohou však obsahovat statický konstruktor. Nestatické třídy by měly také definovat statický konstruktor, pokud třída obsahuje statické členy, které vyžadují netriviální inicializaci. Další informace naleznete v tématu [statické konstruktory](./static-constructors.md).  
  
## <a name="example"></a>Příklad  
 Tady je příklad statické třídy, která obsahuje dvě metody, které převádějí teplotu z Celsia na Fahrenheita a z Fahrenheita na Celsia:  
  
 [!code-csharp[csProgGuideObjects#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#31)]  
  
## <a name="static-members"></a>Statické členy  
 Nestatická třída může obsahovat statické metody, pole, vlastnosti nebo události. Statický člen je volat na třídu, i když nebyla vytvořena žádná instance třídy. K statickému členu se vždy používá název třídy, nikoli název instance. Existuje pouze jedna kopie statického člena bez ohledu na to, kolik instancí třídy je vytvořeno. Statické metody a vlastnosti nemají přístup k nestatickým polím a událostem ve svých nadřazených typech a nemohou přistupovat k proměnné instance žádného objektu, pokud není explicitně předána parametrem metody.  
  
 Je obvyklejší deklarovat nestatickou třídu s některými statickými členy, než deklarovat celou třídu jako statickou. Dvě společná použití statických polí jsou uchovávají počet objektů, které byly vytvořeny instance, nebo ukládají hodnotu, která musí být sdílena mezi všemi instancemi.  
  
 Statické metody mohou být přetíženy, ale nejsou přepsány, protože patří do třídy, a nikoli do žádné instance třídy.  
  
 I když pole nemůže být deklarováno jako `static const` , pole [const](../../language-reference/keywords/const.md) je v podstatě statické v jeho chování. Patří do typu, nikoli do instancí typu. Proto `const` lze k polím přistupovat pomocí stejného `ClassName.MemberName` zápisu, který je použit pro statická pole. Není požadována žádná instance objektu.  
  
 Jazyk C# nepodporuje statické lokální proměnné (tj. proměnné, které jsou deklarovány v oboru metody).  
  
 Statické členy třídy deklarujete pomocí `static` klíčového slova před návratovým typem členu, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideObjects#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#29)]  
  
 Statické členy jsou inicializovány před prvním otevřením statického člena a před statickým konstruktorem, pokud je volána. Chcete-li získat přístup ke členu statické třídy, použijte název třídy namísto názvu proměnné pro určení umístění člena, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideObjects#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#30)]  
  
 Pokud vaše třída obsahuje statická pole, poskytněte statický konstruktor, který je inicializuje při načtení třídy.  
  
 Volání statické metody generuje instrukci volání v jazyce MSIL (Microsoft Intermediate Language), zatímco volání metody instance vygeneruje `callvirt` instrukci, která také kontroluje odkazy na objekty s hodnotou null. Ale ve většině případů není rozdíl mezi výkonem mezi těmito dvěma důležitý.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  

Další informace naleznete v tématu [statické třídy](~/_csharplang/spec/classes.md#static-classes) a [statické a instance členů](~/_csharplang/spec/classes.md#static-and-instance-members) ve [specifikaci jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [static](../../language-reference/keywords/static.md)
- [Třídy](./classes.md)
- [Deník](../../language-reference/keywords/class.md)
- [Statické konstruktory](./static-constructors.md)
- [Konstruktory instancí](./instance-constructors.md)
