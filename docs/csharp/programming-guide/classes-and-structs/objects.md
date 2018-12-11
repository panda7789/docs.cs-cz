---
title: Objekty - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- objects [C#], about objects
- variables [C#]
ms.assetid: af4a5230-fbf3-4eea-95e1-8b883c2f845c
ms.openlocfilehash: 439f001450d51885f943cb28752de1689dd4a748
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235095"
---
# <a name="objects-c-programming-guide"></a>Objekty (Průvodce programováním v C#)
Definice třídy nebo struktury je jako matrice, který určuje, co můžete dělat typu. Objekt je v podstatě blok paměti, která byla přidělena a nakonfigurovány podle podrobný plán. Program může vytvořit mnoho objektů stejné třídy. Objekty se také označují jako instance a mohou být uloženy v pojmenované proměnné nebo v poli nebo kolekci. Klientský kód je kód, který používá tyto proměnné pro volání metody a přístup k veřejné vlastnosti objektu. V jazyce objektově orientované jako je C# typický program se skládá z více objektů dynamicky interakci.  
  
> [!NOTE]
>  Statické typy chovat jinak než jak je popsán tady. Další informace najdete v tématu [statické třídy a statické členy třídy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
## <a name="struct-instances-vs-class-instances"></a>Struktura instance vs. Instance třídy  
 Vzhledem k tomu, že třídy jsou odkazové typy, proměnné objektu třídy obsahuje odkaz na adresu objektu na spravované haldě. Pokud se první objekt, který je přiřazen druhému objektu stejného typu, pak obě proměnné odkazovat na objekt na této adrese. Tento bod je podrobněji popsány dále v tomto tématu.  
  
 Instance třídy se vytvářejí pomocí [operátor new](../../../csharp/language-reference/keywords/new-operator.md). V následujícím příkladu `Person` je typ a `person1` a `person 2` instance ani objekty daného typu.  
  
 [!code-csharp[csProgGuideStatements#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_1.cs)]  
  
 Protože struktury jsou typy hodnot, proměnné objektu struktura obsahuje kopii celého objektu. Instance struktury můžete vytvořit také pomocí `new` operátoru, ale to se nevyžaduje, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideStatements#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_2.cs)]  
  
 Paměť pro obě `p1` a `p2` přidělené v zásobníku vlákna. Tuto paměť je uvolněn spolu se tento typ nebo metoda, ve kterém je deklarována. Toto je jedním z důvodů, proč strukturách kopírují na přiřazení. Naopak paměti přidělené pro instanci třídy, je automaticky uvolňovaného (uvolněna z paměti) modul common language runtime při všech odkazů na objekt nepřejdou mimo rozsah. Není možné nedeterministicky zničit objekt třídy jako můžete v jazyce C++. Další informace o uvolňování paměti v [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], naleznete v tématu [uvolňování](../../../standard/garbage-collection/index.md).  
  
> [!NOTE]
>  V modulu common language runtime je vysoce optimalizovaných přidělování a navracení zpět paměti na spravované haldě. Ve většině případů není žádný velký rozdíl náklady na výkon spojeným s přidělováním instance třídy v haldě a přidělování struktury instance v zásobníku.  
  
## <a name="object-identity-vs-value-equality"></a>Objekt Identity vs. Hodnota rovnosti  
 Když porovnáte dva objekty z hlediska rovnosti, musí nejprve rozlišit, jestli chcete zjistit, jestli dvě proměnné, které představují stejný objekt v paměti nebo zda jsou ekvivalentní hodnoty jedné nebo více z jejich polí. Pokud je máte v úmyslu porovnat hodnoty, musíte zvážit, zda jsou objekty instance typů hodnot (struktury) nebo typy odkazů (tříd, delegátů, pole).  
  
-   K určení, zda dvě instance třídy odkazují na stejné místo v paměti (což znamená, že mají stejnou *identity*), použít statické <xref:System.Object.Equals%2A> metody. (<xref:System.Object?displayProperty=nameWithType> je implicitní základní třída pro všechny typy hodnot a odkazové typy, včetně uživatelem definované strukturám a třídám.)  
  
-   Chcete-li zjistit, zda pole instancí ve dvou instancí struktury mají stejné hodnoty, použijte <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> metody. Protože implicitně dědí všechny struktury <xref:System.ValueType?displayProperty=nameWithType>, zavolejte metodu přímo na objekt, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideStatements#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_3.cs)]  
  
 <xref:System.ValueType?displayProperty=nameWithType> Provádění `Equals` používá reflexi, protože musí být schopní určit pole jsou v libovolné struktury. Při vytváření vlastních struktur, přepsat `Equals` metodu k dispozici efektivní rovnosti algoritmus, který je specifický pro váš typ.  
  
-   Pokud chcete zjistit, zda jsou stejné hodnoty polí v dvě instance třídy, je možné použít <xref:System.Object.Equals%2A> metoda nebo [== – operátor](../../../csharp/language-reference/operators/equality-comparison-operator.md). Ale pouze používejte, je pokud třída má přepsat nebo přetížené jim poskytnout vlastní definici z jaké "rovnosti" znamená, že objekty tohoto typu. Třída může implementovat taky <xref:System.IEquatable%601> rozhraní nebo <xref:System.Collections.Generic.IEqualityComparer%601> rozhraní. Obě rozhraní poskytuje metody, které můžete použít k testování rovnosti hodnoty. Při navrhování vlastních tříd toto přepsání `Equals`, ujistěte se, že dodržovat pokyny uvedené v [jak: Definování rovnosti hodnoty pro typ](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md) a <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>.  
  
## <a name="related-sections"></a>Související oddíly  
 Další informace:  
  
-   [Třídy](../../../csharp/programming-guide/classes-and-structs/classes.md)  
  
-   [Struktury](../../../csharp/programming-guide/classes-and-structs/structs.md)  
  
-   [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [Finalizační metody](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
  
-   [Události](../../../csharp/programming-guide/events/index.md)  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [object](../../../csharp/language-reference/keywords/object.md)  
- [Dědičnost](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
- [class](../../../csharp/language-reference/keywords/class.md)  
- [struct](../../../csharp/language-reference/keywords/struct.md)  
- [new – operátor](../../../csharp/language-reference/keywords/new-operator.md)  
- [Obecný systém typů](../../../standard/base-types/common-type-system.md)
