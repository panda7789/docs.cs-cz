---
title: Objekty – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- objects [C#], about objects
- variables [C#]
ms.assetid: af4a5230-fbf3-4eea-95e1-8b883c2f845c
ms.openlocfilehash: 3319cfa6b98e3f4b9b8afa070c4784c03d2750ef
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596384"
---
# <a name="objects-c-programming-guide"></a>Objekty (Průvodce programováním v C#)
Definice třídy nebo struktury je jako podrobný plán, který určuje, co může typ provádět. Objekt je v podstatě blok paměti, který byl přidělen a nakonfigurován podle podrobného plánu. Program může vytvořit mnoho objektů stejné třídy. Objekty se také nazývají instance a mohou být uloženy buď v pojmenované proměnné, nebo v poli nebo v kolekci. Kód klienta je kód, který používá tyto proměnné pro volání metod a přístup k veřejným vlastnostem objektu. V objektově orientovaném jazyce C#, jako je typický program, se skládá z více objektů, které pracují dynamicky.  
  
> [!NOTE]
> Statické typy se chovají jinak, než je popsáno zde. Další informace naleznete v tématu [statické třídy a statické členy třídy](./static-classes-and-static-class-members.md).
  
## <a name="struct-instances-vs-class-instances"></a>Instance struktury vs. Instance třídy  
 Vzhledem k tomu, že třídy jsou odkazové typy, proměnná objektu třídy obsahuje odkaz na adresu objektu na spravované haldě. Pokud je druhý objekt stejného typu přiřazen k prvnímu objektu, pak obě proměnné odkazují na objekt na dané adrese. Tento bod je podrobněji popsán dále v tomto tématu.  
  
 Instance tříd jsou vytvořeny pomocí [operátoru new](../../language-reference/operators/new-operator.md). V následujícím příkladu `Person` je typ a `person1` a `person 2` jsou instance nebo objekty daného typu.  
  
 [!code-csharp[csProgGuideStatements#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#30)]  
  
 Vzhledem k tomu, že struktury jsou typy hodnot, proměnná objektu struct obsahuje kopii celého objektu. Instance struktur lze také vytvořit pomocí `new` operátoru, ale to není vyžadováno, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideStatements#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#31)]  
  
 Paměť pro obojí `p1` a `p2` je přidělena v zásobníku vláken. Tato paměť je uvolněna spolu s typem nebo metodou, ve které je deklarována. Toto je jeden z důvodů, proč se struktury zkopírují při přiřazení. Naproti tomu paměť, která je přidělena instanci třídy, je automaticky uvolněna (uvolňování paměti) modulem CLR (Common Language Runtime), pokud všechny odkazy na objekt prošly mimo rozsah. Není možné deterministické zničení objektu třídy, jako můžete v C++. Další informace o uvolňování paměti v .NET Framework najdete v tématu [uvolňování paměti](../../../standard/garbage-collection/index.md).  
  
> [!NOTE]
> Přidělování a navracení paměti ve spravované haldě je vysoce optimalizované v modulu CLR (Common Language Runtime). Ve většině případů nedochází k výraznému rozdílu v nákladech na výkon při přidělování instance třídy na haldě a při přidělování instance struktury v zásobníku.
  
## <a name="object-identity-vs-value-equality"></a>Identita objektu vs. Hodnota rovnosti  
 Když porovnáte dva objekty pro rovnost, musíte nejprve rozlišovat, zda chcete zjistit, zda tyto dvě proměnné představují stejný objekt v paměti nebo zda jsou hodnoty jednoho nebo více jejich polí ekvivalentní. Pokud hodláte porovnat hodnoty, je nutné vzít v úvahu, zda jsou objekty instance typů hodnot (struktury) nebo typy odkazů (třídy, delegáti, pole).  
  
- Chcete-li zjistit, zda dvě instance třídy odkazují na stejné umístění v paměti (což znamená, že mají stejnou *identitu*), použijte statickou <xref:System.Object.Equals%2A> metodu. (<xref:System.Object?displayProperty=nameWithType> je implicitní základní třída pro všechny typy hodnot a odkazové typy, včetně uživatelsky definovaných struktur a tříd.)  
  
- Chcete-li zjistit, zda pole instance ve dvou instancích struktury mají stejné hodnoty, <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> použijte metodu. Vzhledem k tomu, že všechny struktury implicitně dědí z <xref:System.ValueType?displayProperty=nameWithType>, zavoláte metodu přímo na objekt, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideStatements#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#32)]  
  
 <xref:System.ValueType?displayProperty=nameWithType> Implementacepoužitíreflexepoužívá,protožemusíbýtschopnaurčit,copole`Equals` jsou v libovolné struktuře. Při vytváření vlastních struktur přepište `Equals` metodu pro poskytnutí efektivního algoritmu rovnosti, který je specifický pro váš typ.  
  
- Chcete-li určit, zda jsou hodnoty polí ve dvou instancích třídy stejné, je možné použít <xref:System.Object.Equals%2A> metodu nebo [operátor = =](../../language-reference/operators/equality-operators.md#equality-operator-). Je však možné je použít pouze v případě, že třída přepsala nebo přetížena k poskytnutí vlastní definice toho, co "rovnost" znamená pro objekty daného typu. Třída může také implementovat <xref:System.IEquatable%601> rozhraní <xref:System.Collections.Generic.IEqualityComparer%601> nebo rozhraní. Obě rozhraní poskytují metody, které lze použít k testování rovnosti hodnoty. Při návrhu vlastních tříd, které jsou `Equals`přepsány, se ujistěte, že dodržujete pokyny uvedené v [tématu How to: Definujte rovnost hodnoty pro typ](../statements-expressions-operators/how-to-define-value-equality-for-a-type.md) a. <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>  
  
## <a name="related-sections"></a>Související oddíly  
 Další informace:  
  
- [Třídy](./classes.md)  
  
- [Struktury](./structs.md)  
  
- [Konstruktory](./constructors.md)  
  
- [Finalizační metody](./destructors.md)  
  
- [Události](../events/index.md)  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [object](../../language-reference/keywords/object.md)
- [Dědičnost](./inheritance.md)
- [class](../../language-reference/keywords/class.md)
- [struct](../../language-reference/keywords/struct.md)
- [new – operátor](../../language-reference/operators/new-operator.md)
- [Obecný systém typů](../../../standard/base-types/common-type-system.md)
