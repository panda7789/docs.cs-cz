---
title: Průvodce programováním objektů – C#
ms.date: 07/20/2015
helpviewer_keywords:
- objects [C#], about objects
- variables [C#]
ms.assetid: af4a5230-fbf3-4eea-95e1-8b883c2f845c
ms.openlocfilehash: 09b290713f3bc2a7a7824bb19c98138943ad5b2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77673378"
---
# <a name="objects-c-programming-guide"></a>Objekty (Průvodce programováním v C#)
Definice třídy nebo struktury je jako podrobný plán, který určuje, co může typ provést. Objekt je v podstatě blok paměti, který byl přidělen a nakonfigurován podle podrobného plánu. Program může vytvořit mnoho objektů stejné třídy. Objekty se také nazývají instance a mohou být uloženy v pojmenované proměnné nebo v poli nebo kolekci. Klientský kód je kód, který používá tyto proměnné k volání metod a přístup u veřejných vlastností objektu. V objektově orientovaném jazyce, například c#, se typický program skládá z více objektů, které dynamicky interagují.  
  
> [!NOTE]
> Statické typy se chovají jinak, než je popsáno zde. Další informace naleznete [v tématu Statické třídy a statické členy třídy](./static-classes-and-static-class-members.md).
  
## <a name="struct-instances-vs-class-instances"></a>Instance struktury vs. instance tříd  
 Vzhledem k tomu, že třídy jsou typy odkazů, proměnná objektu třídy obsahuje odkaz na adresu objektu na spravované haldě. Pokud druhý objekt stejného typu je přiřazen k prvnímu objektu, pak obě proměnné odkazují na objekt na této adrese. Tento bod je podrobněji popsán dále v tomto tématu.  
  
 Instance tříd jsou vytvářeny pomocí [nového operátoru](../../language-reference/operators/new-operator.md). V následujícím příkladu `Person` je `person1` typ `person 2` a a jsou instance nebo objekty tohoto typu.  
  
 [!code-csharp[csProgGuideStatements#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#30)]  
  
 Vzhledem k tomu, že struktury jsou typy hodnot, proměnná objektu struktury obsahuje kopii celého objektu. Instance struktur lze také vytvořit pomocí operátoru, `new` ale to není vyžadováno, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideStatements#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#31)]  
  
 Paměť pro `p1` oba `p2` a je přidělena v zásobníku podprocesu. Tato paměť je rekultivována spolu s typem nebo metodou, ve které je deklarována. To je jeden z důvodů, proč jsou struktury zkopírovány při přiřazení. Naproti tomu paměť, která je přidělena pro instanci třídy je automaticky uvolněna (uvolňování uvolňování) v běžném jazyku runtime při všechny odkazy na objekt byly mimo rozsah. Není možné deterministicky zničit objekt třídy, jako můžete v jazyce C++. Další informace o uvolňování paměti v rozhraní .NET Framework naleznete v tématu [Garbage Collection](../../../standard/garbage-collection/index.md).  
  
> [!NOTE]
> Přidělení a přidělení paměti na spravované haldy je vysoce optimalizovánv prostředí common language runtime. Ve většině případů neexistuje žádný významný rozdíl v nákladech na výkon přidělení instance třídy na haldě versus přidělení instance struktury v zásobníku.
  
## <a name="object-identity-vs-value-equality"></a>Identita objektu vs. rovnost hodnot  
 Při porovnání dva objekty rovnosti, musíte nejprve rozlišit, zda chcete vědět, zda dvě proměnné představují stejný objekt v paměti, nebo zda hodnoty jednoho nebo více jejich polí jsou ekvivalentní. Pokud máte v úmyslu porovnat hodnoty, je třeba zvážit, zda objekty jsou instance typy hodnot (struktury) nebo typy odkazů (třídy, delegáti, pole).  
  
- Chcete-li zjistit, zda dvě instance třídy odkazují na stejné umístění v paměti <xref:System.Object.Equals%2A> (což znamená, že mají stejnou *identitu*), použijte statickou metodu. (<xref:System.Object?displayProperty=nameWithType> je implicitní základní třída pro všechny typy hodnot a typy odkazů, včetně uživatelem definovaných struktur a tříd.)  
  
- Chcete-li zjistit, zda mají pole instance ve dvou <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> instancích struktury stejné hodnoty, použijte metodu. Protože všechny struktury implicitně <xref:System.ValueType?displayProperty=nameWithType>dědí z , zavoláte metodu přímo na objekt, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideStatements#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#32)]  
  
 Implementace <xref:System.ValueType?displayProperty=nameWithType> používá `Equals` reflexe, protože musí být schopen určit, jaké pole jsou v libovolné struktuře. Při vytváření vlastnístruktury, přepsat metodu `Equals` poskytnout algoritmus efektivní rovnosti, která je specifická pro váš typ.  
  
- Chcete-li zjistit, zda jsou hodnoty polí ve dvou instancích <xref:System.Object.Equals%2A> třídy stejné, můžete použít metodu nebo [operátor ==](../../language-reference/operators/equality-operators.md#equality-operator-). Však používejte pouze v případě, že třída má přepsány nebo přetížené je poskytnout vlastní definici co "rovnost" znamená pro objekty tohoto typu. Třída může také <xref:System.IEquatable%601> implementovat <xref:System.Collections.Generic.IEqualityComparer%601> rozhraní nebo rozhraní. Obě rozhraní poskytují metody, které lze použít k testování rovnosti hodnot. Při navrhování vlastní třídy, `Equals`které přepsat , ujistěte se, že postupujte podle pokynů uvedených v [Jak definovat rovnost hodnot pro typ](../statements-expressions-operators/how-to-define-value-equality-for-a-type.md) a <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>.
  
## <a name="related-sections"></a>Související oddíly  
 Další informace najdete tady:  
  
- [Třídy](./classes.md)  
  
- [Konstruktory](./constructors.md)  
  
- [Finalizační metody](./destructors.md)  
  
- [Akce](../events/index.md)  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Objekt](../../language-reference/builtin-types/reference-types.md)
- [Dědičnost](./inheritance.md)
- [Třída](../../language-reference/keywords/class.md)
- [Typy struktur](../../language-reference/builtin-types/struct.md)
- [new – operátor](../../language-reference/operators/new-operator.md)
- [Obecný systém typů](../../../standard/base-types/common-type-system.md)
