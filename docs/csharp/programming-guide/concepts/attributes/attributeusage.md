---
title: AttributeUsage (C#)
ms.date: 04/25/2018
ms.openlocfilehash: a3a82e33d7259ec56ec3e907bc3d4d9f8a01167d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "61668715"
---
# <a name="attributeusage-c"></a>AttributeUsage (C#)

Určuje, jak lze použít vlastní třídu atributů. <xref:System.AttributeUsageAttribute>je atribut, který aplikujete na vlastní definice atributů. Atribut `AttributeUsage` umožňuje řídit:

- U kterých programových prvků může být atribut použit. Pokud neomezíte jeho použití, může být atribut použit na některý z následujících prvků programu:
  - sestavení
  - module
  - pole
  - event
  - method
  - Param
  - property
  - return
  - type
- Určuje, zda lze atribut použít na jeden prvek programu vícekrát.
- Určuje, zda jsou atributy zděděny odvozenými třídami.

Výchozí nastavení vypadá jako v následujícím příkladu při explicitním použití:

[!code-csharp[Define a new attribute](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#1)]

V tomto příkladu lze třídu `NewAttribute` použít na libovolný podporovaný prvek programu. Ale to může být použita pouze jednou pro každou entitu. Atribut je zděděn odvozenými třídami při použití na základní třídu.

A <xref:System.AttributeUsageAttribute.AllowMultiple> <xref:System.AttributeUsageAttribute.Inherited> argumenty jsou volitelné, takže následující kód má stejný účinek:

[!code-csharp[Omit optional attributes](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#2)]

První <xref:System.AttributeUsageAttribute> argument musí být jeden nebo <xref:System.AttributeTargets> více prvků výčtu. Více typů cílů lze propojit společně s operátorem OR, jako je následující příklad:

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#1)]

Počínaje C# 7.3, atributy lze použít buď vlastnost nebo záložní pole pro automaticky implementované vlastnosti. Atribut se vztahuje na vlastnost, pokud `field` nezadáte specifikátor atributu. Obě jsou uvedeny v následujícím příkladu:

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#2)]

Pokud <xref:System.AttributeUsageAttribute.AllowMultiple> je `true`argument , pak výsledný atribut lze použít více než jednou na jednu entitu, jak je znázorněno v následujícím příkladu:

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/MultiUseAttribute.cs#1)]

V tomto `MultiUseAttribute` případě lze použít `AllowMultiple` opakovaně, `true`protože je nastavena na . Oba formáty zobrazené pro použití více atributů jsou platné.

Pokud <xref:System.AttributeUsageAttribute.Inherited> `false`je , pak atribut není zděděn podle tříd odvozených z atributu třídy. Například:

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/NonInheritedAttribute.cs#1)]

V tomto `NonInheritedAttribute` případě se `DClass` nevztahuje na prostřednictvím dědičnosti.

## <a name="remarks"></a>Poznámky

Atribut `AttributeUsage` je atribut na jedno použití – nelze jej použít více než jednou na stejnou třídu. `AttributeUsage`je alias <xref:System.AttributeUsageAttribute>pro aplikaci .

Další informace naleznete [v tématu Přístup k atributům pomocí reflexe (C#)](accessing-attributes-by-using-reflection.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje účinek <xref:System.AttributeUsageAttribute.Inherited> a <xref:System.AttributeUsageAttribute.AllowMultiple> argumenty <xref:System.AttributeUsageAttribute> na atribut a jak lze vyjmenovat vlastní atributy použité pro třídu.

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

- <xref:System.Attribute>
- <xref:System.Reflection>
- [Programovací příručka jazyka C#](../..//index.md)
- [Atributy](../../../..//standard/attributes/index.md)
- [Reflexe (C#)](../reflection.md)
- [Atributy](index.md)
- [Vytváření vlastních atributů (C#)](creating-custom-attributes.md)
- [Přístup k atributům pomocí reflexe (C#)](accessing-attributes-by-using-reflection.md)
