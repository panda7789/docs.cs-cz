---
title: Objekty – Průvodce programováním v C#
ms.date: 07/20/2015
helpviewer_keywords:
- objects [C#], about objects
- variables [C#]
ms.assetid: af4a5230-fbf3-4eea-95e1-8b883c2f845c
ms.openlocfilehash: a9411557e9177c8dbed45ec25984d574479da0de
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241783"
---
# <a name="objects-c-programming-guide"></a>Objekty (Průvodce programováním v C#)
Definice třídy nebo struktury je jako podrobný plán, který určuje, co může typ provádět. Objekt je v podstatě blok paměti, který byl přidělen a nakonfigurován podle podrobného plánu. Program může vytvořit mnoho objektů stejné třídy. Objekty se také nazývají instance a mohou být uloženy buď v pojmenované proměnné, nebo v poli nebo v kolekci. Kód klienta je kód, který používá tyto proměnné pro volání metod a přístup k veřejným vlastnostem objektu. V objektově orientovaném jazyce, jako je C#, typický program sestává z více objektů, které projednají dynamicky.  
  
> [!NOTE]
> Statické typy se chovají jinak, než je popsáno zde. Další informace naleznete v tématu [statické třídy a statické členy třídy](./static-classes-and-static-class-members.md).
  
## <a name="struct-instances-vs-class-instances"></a>Instance struktury vs. instance třídy  
 Vzhledem k tomu, že třídy jsou odkazové typy, proměnná objektu třídy obsahuje odkaz na adresu objektu na spravované haldě. Pokud je druhý objekt stejného typu přiřazen k prvnímu objektu, pak obě proměnné odkazují na objekt na dané adrese. Tento bod je podrobněji popsán dále v tomto tématu.  
  
 Instance tříd jsou vytvořeny pomocí [operátoru new](../../language-reference/operators/new-operator.md). V následujícím příkladu `Person` je typ a `person1` a `person 2` jsou instance nebo objekty daného typu.  
  
 [!code-csharp[csProgGuideStatements#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#30)]  
  
 Vzhledem k tomu, že struktury jsou typy hodnot, proměnná objektu struct obsahuje kopii celého objektu. Instance struktur lze také vytvořit pomocí `new` operátoru, ale to není vyžadováno, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideStatements#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#31)]  
  
 Paměť pro obojí `p1` a `p2` je přidělena v zásobníku vláken. Tato paměť je uvolněna spolu s typem nebo metodou, ve které je deklarována. Toto je jeden z důvodů, proč se struktury zkopírují při přiřazení. Naproti tomu paměť, která je přidělena instanci třídy, je automaticky uvolněna (uvolňování paměti) modulem CLR (Common Language Runtime), pokud všechny odkazy na objekt prošly mimo rozsah. Objekt třídy není možné deterministickém způsobem odstranit, jako v jazyce C++. Další informace o uvolňování paměti v rozhraní .NET najdete v tématu [uvolňování paměti](../../../standard/garbage-collection/index.md).  
  
> [!NOTE]
> Přidělování a navracení paměti ve spravované haldě je vysoce optimalizované v modulu CLR (Common Language Runtime). Ve většině případů nedochází k výraznému rozdílu v nákladech na výkon při přidělování instance třídy na haldě a při přidělování instance struktury v zásobníku.
  
## <a name="object-identity-vs-value-equality"></a>Identita objektu vs. hodnota rovnosti  
 Když porovnáte dva objekty pro rovnost, musíte nejprve rozlišovat, zda chcete zjistit, zda tyto dvě proměnné představují stejný objekt v paměti nebo zda jsou hodnoty jednoho nebo více jejich polí ekvivalentní. Pokud hodláte porovnat hodnoty, je nutné vzít v úvahu, zda jsou objekty instance typů hodnot (struktury) nebo typy odkazů (třídy, delegáti, pole).  
  
- Chcete-li zjistit, zda dvě instance třídy odkazují na stejné umístění v paměti (což znamená, že mají stejnou *identitu*), použijte statickou <xref:System.Object.Equals%2A> metodu. ( <xref:System.Object?displayProperty=nameWithType> je implicitní základní třída pro všechny typy hodnot a odkazové typy, včetně uživatelsky definovaných struktur a tříd.)  
  
- Chcete-li zjistit, zda pole instance ve dvou instancích struktury mají stejné hodnoty, použijte <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> metodu. Vzhledem k tomu, že všechny struktury implicitně dědí z <xref:System.ValueType?displayProperty=nameWithType> , zavoláte metodu přímo na objekt, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideStatements#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#32)]  
  
 <xref:System.ValueType?displayProperty=nameWithType>Implementace `Equals` použití reflexe používá, protože musí být schopna určit, co pole jsou v libovolné struktuře. Při vytváření vlastních struktur přepište `Equals` metodu pro poskytnutí efektivního algoritmu rovnosti, který je specifický pro váš typ.  
  
- Chcete-li určit, zda jsou hodnoty polí ve dvou instancích třídy stejné, je možné použít <xref:System.Object.Equals%2A> metodu nebo [operátor = =](../../language-reference/operators/equality-operators.md#equality-operator-). Je však možné je použít pouze v případě, že třída přepsala nebo přetížena k poskytnutí vlastní definice toho, co "rovnost" znamená pro objekty daného typu. Třída může také implementovat <xref:System.IEquatable%601> rozhraní nebo <xref:System.Collections.Generic.IEqualityComparer%601> rozhraní. Obě rozhraní poskytují metody, které lze použít k testování rovnosti hodnoty. Při návrhu vlastních tříd, které jsou přepsány `Equals` , se ujistěte, že je nutné postupovat podle pokynů uvedených v tématu [jak definovat hodnotu rovnosti pro typ](../statements-expressions-operators/how-to-define-value-equality-for-a-type.md) a <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> .
  
## <a name="related-sections"></a>Související oddíly  
 Další informace najdete tady:  
  
- [Třídy](./classes.md)  
  
- [Konstruktory](./constructors.md)  
  
- [Finalizační metody](./destructors.md)  
  
- [Události](../events/index.md)  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [odkazy objektů](../../language-reference/builtin-types/reference-types.md)
- [Dědičnost](./inheritance.md)
- [Deník](../../language-reference/keywords/class.md)
- [Typy struktur](../../language-reference/builtin-types/struct.md)
- [New – operátor](../../language-reference/operators/new-operator.md)
- [Běžný systém typů](../../../standard/base-types/common-type-system.md)
