---
title: Objekty (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- objects [C#], about objects
- variables [C#]
ms.assetid: af4a5230-fbf3-4eea-95e1-8b883c2f845c
ms.openlocfilehash: 553b0a5e75364bc5c294867852265575fb9271b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33324672"
---
# <a name="objects-c-programming-guide"></a>Objekty (Průvodce programováním v C#)
Definice třídě nebo struktuře je jako matrici, která určuje, co můžete dělat typu. Objekt je v podstatě blok paměti, která je přidělena a nakonfigurovaný podle plánu. Program může vytvořit mnoho objektů stejné třídy. Objekty jsou také označovány jako instance a mohou být uloženy v proměnnou s názvem nebo v pole nebo kolekce. Kód klienta je kód, který používá tyto proměnné volání metody a přístup k veřejné vlastnosti objektu. V jazyce objektově orientované například C# typické program se skládá z více objektů dynamicky interakci.  
  
> [!NOTE]
>  Statické typy chovat jinak než co je zde popsán. Další informace najdete v tématu [statické třídy a statické členy třídy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
## <a name="struct-instances-vs-class-instances"></a>Struktura instancí vs. Instance třídy  
 Protože třídy jsou odkazové typy, proměnné objektu třídy obsahuje odkaz na adresu objektu na spravované haldě. Pokud druhý objekt stejného typu, je přiřazen k první objekt, obě proměnné odkazovat na objekt na této adrese. Tento bod je podrobněji popsána dále v tomto tématu.  
  
 Instance třídy jsou vytvořené pomocí [operátor new](../../../csharp/language-reference/keywords/new-operator.md). V následujícím příkladu `Person` je typ a `person1` a `person 2` instance ani objekty daného typu.  
  
 [!code-csharp[csProgGuideStatements#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_1.cs)]  
  
 Protože struktury jsou typy hodnot, proměnné objektu struktura obsahuje kopii celý objekt. Instance struktury můžete také vytvořit pomocí `new` operátor, ale to není požadováno, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideStatements#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_2.cs)]  
  
 Paměť pro obě `p1` a `p2` je přidělená v zásobníku přístup z více vláken. Tuto paměť je uvolnit společně s typ nebo metoda, ve kterém je deklarovaná. Toto je jedním z důvodů, proč struktury zkopírují na přiřazení. Naopak paměti, která je přidělena pro instanci třídy je automaticky regenerovaný (uvolnění z paměti) modul common language runtime při všechny odkazy na objekt se nachází mimo obor. Není možné nepodmíněně odstranění objektu třídy, jako je možné v jazyce C++. Další informace o uvolňování paměti v [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], najdete v části [uvolňování paměti](../../../standard/garbage-collection/index.md).  
  
> [!NOTE]
>  Přidělení a zrušení přidělení paměti na spravovaná halda je vysoce optimalizovaný v modulu CLR. Ve většině případů není žádné významné rozdíl ve výkonu náklady přidělování v haldě versus přidělování struktura instance v zásobníku instance třídy.  
  
## <a name="object-identity-vs-value-equality"></a>Objekt Identity vs. Hodnota rovnosti  
 Při porovnávání dva objekty z hlediska rovnosti musí nejprve rozlišovat, jestli chcete zjistit, jestli dvě proměnné, které představují stejný objekt v paměti, nebo zda hodnoty jednoho nebo více jejich polí jsou ekvivalentní. Pokud se hodláte porovnat hodnoty, musíte zvážit, jestli jsou objekty instancí typy hodnot (struktury) nebo odkazové typy (třídy, delegáti, pole).  
  
-   K určení, zda dvě instance třídy odkazovat na stejné umístění v paměti (což znamená, že mají stejný *identity*), použijte statickou <xref:System.Object.Equals%2A> metoda. (<xref:System.Object?displayProperty=nameWithType> je implicitní základní třída pro všechny typy hodnot a typy odkazu, včetně uživatelem definované strukturám a třídám.)  
  
-   Chcete-li zjistit, jestli pole instance v dvě instance struktura mají stejné hodnoty, použijte <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> metoda. Protože všechny struktury implicitně dědí <xref:System.ValueType?displayProperty=nameWithType>, zavolejte metodu přímo na objektu, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideStatements#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_3.cs)]  
  
 <xref:System.ValueType?displayProperty=nameWithType> Implementace `Equals` používá reflexe, protože musí být schopní určit, co jsou tato pole v jakékoli struktura. Při vytváření vlastní struktury, přepsat `Equals` metody můžete zajistit efektivní rovnosti algoritmu, který je určený výhradně pro vašeho typu.  
  
-   Pokud chcete zjistit, zda jsou stejné hodnoty polí v dvě instance třídy, je možné použít <xref:System.Object.Equals%2A> metoda nebo [== – operátor](../../../csharp/language-reference/operators/equality-comparison-operator.md). Však použijte jenom je pokud třída má přepsat nebo přetížený mají poskytovat vlastní definice jaké "rovnosti" znamená, že pro objekty daného typu. Třída může také implementovat <xref:System.IEquatable%601> rozhraní nebo <xref:System.Collections.Generic.IEqualityComparer%601> rozhraní. Obě rozhraní poskytují metody, které lze použít k testování rovnosti hodnoty. Při navrhování vlastních tříd této přepsání `Equals`, ujistěte se, postupujte podle pokynů uvádí [postupy: definování rovnosti hodnoty pro typ](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md) a <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>.  
  
## <a name="related-sections"></a>Související oddíly  
 Další informace:  
  
-   [Třídy](../../../csharp/programming-guide/classes-and-structs/classes.md)  
  
-   [Struktury](../../../csharp/programming-guide/classes-and-structs/structs.md)  
  
-   [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [Finalizační metody](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
  
-   [Události](../../../csharp/programming-guide/events/index.md)  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [object](../../../csharp/language-reference/keywords/object.md)  
 [Dědičnost](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
 [class](../../../csharp/language-reference/keywords/class.md)  
 [struct](../../../csharp/language-reference/keywords/struct.md)  
 [new – operátor](../../../csharp/language-reference/keywords/new-operator.md)  
 [Obecný systém typů](../../../standard/base-types/common-type-system.md)
