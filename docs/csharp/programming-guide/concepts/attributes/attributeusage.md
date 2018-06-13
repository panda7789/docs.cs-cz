---
title: AttributeUsage (C#)
ms.date: 04/25/2018
ms.openlocfilehash: 869e6509e55268767915a783a8652f7f950d7137
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
ms.locfileid: "33955925"
---
# <a name="attributeusage-c"></a>AttributeUsage (C#)

Určuje, jak lze použít třídu vlastního atributu. <xref:System.AttributeUsageAttribute> je atribut, který použijete pro definice vlastních atributů. `AttributeUsage` Atributů umožňují řídit:

- Který atribut elementy program může použít. Pokud omezíte je využití atribut je možné používat k jakémukoli z těchto prvků program:
  - sestavení
  - module
  - pole
  - event
  - – metoda
  - Param
  - property
  - return
  - – typ
- Více než jednou. jestli chcete v jednom elementu programu je použít atribut.
- Zda jsou zdědí atributy odvozené třídy.

Výchozí nastavení vypadat podobně jako v následujícím příkladu při použití explicitně:

[!code-csharp[Define a new attribute](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#1)]

V tomto příkladu `NewAttribute` třídy lze použít na všech podporovaných program element. Ale dá se použít jenom jednou pro každé entity. Atribut zdědí odvozené třídy při použití základní třídy.

<xref:System.AttributeUsageAttribute.AllowMultiple> a <xref:System.AttributeUsageAttribute.Inherited> jsou argumenty nepovinné, takže stejného efektu má následující kód:

[!code-csharp[Omit optional attributes](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#2)]

První <xref:System.AttributeUsageAttribute> argument musí být jeden či více elementů <xref:System.AttributeTargets> výčtu. Více typy cíle může být propojený společně s operátoru OR, jako ukazuje následující příklad:

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#1)]

Počínaje 7.3 C#, můžete použít atributů vlastnost nebo pole Základní automaticky implementované vlastnosti. Atribut se vztahují na vlastnost, pokud nezadáte `field` specifikátor na atributu. Jak se zobrazuje v následujícím příkladu:

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#2)]

Pokud <xref:System.AttributeUsageAttribute.AllowMultiple> argument je `true`, pak výsledné atribut můžete použít více než jednou pro jednu entitu, jak je znázorněno v následujícím příkladu:

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/MultiUseAttribute.cs#1)]

V takovém případě `MultiUseAttribute` můžete použít opakovaně, protože `AllowMultiple` je nastaven na `true`. Platné jsou oba formáty pro použití více atributů.

Pokud <xref:System.AttributeUsageAttribute.Inherited> je `false`, pak atribut není zdědí třídy odvozené od s atributy třídy. Příklad:

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/NonInheritedAttribute.cs#1)]

V takovém případě `NonInheritedAttribute` neplatí pro `DClass` prostřednictvím dědičnosti.

## <a name="remarks"></a>Poznámky

`AttributeUsage` Se o jedno použití atribut – jej nelze použít více než jednou pro stejnou třídu. `AttributeUsage` je alias <xref:System.AttributeUsageAttribute>.

Další informace najdete v tématu [přístup k atributy podle pomocí reflexe (C#)](accessing-attributes-by-using-reflection.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje účinek <xref:System.AttributeUsageAttribute.Inherited> a <xref:System.AttributeUsageAttribute.AllowMultiple> argumenty, které mají <xref:System.AttributeUsageAttribute> atribut a jak mohou být uvedené vlastních atributů použitých na třídu.

[!code-csharp[Applying and querying attributes](../../../../../samples/snippets/csharp/attributes/Program.cs#1)]

## <a name="sample-output"></a>Vzorový výstup

```text
Attributes on Base Class:
FirstAttribute
SecondAttribute
Attributes on Derived Class:
ThirdAttribute
ThirdAttribute
SecondAttribute
```

## <a name="see-also"></a>Viz také
 <xref:System.Attribute>  
 <xref:System.Reflection>  
 [Průvodce programováním v jazyce C#](../..//index.md)  
 [Atributy](../../../..//standard/attributes/index.md)  
 [Reflexe (C#)](../reflection.md)  
 [Atributy](index.md)  
 [Vytváření vlastních atributů (C#)](creating-custom-attributes.md)  
 [Přístup k atributům pomocí reflexe (C#)](accessing-attributes-by-using-reflection.md)
