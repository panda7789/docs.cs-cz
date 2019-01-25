---
title: AttributeUsage (C#)
ms.date: 04/25/2018
ms.openlocfilehash: a3a82e33d7259ec56ec3e907bc3d4d9f8a01167d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589308"
---
# <a name="attributeusage-c"></a>AttributeUsage (C#)

Určuje, jak je možné třídu vlastního atributu. <xref:System.AttributeUsageAttribute> představuje atribut, které použijete pro vlastní atribut definice. `AttributeUsage` Atribut umožňuje řídit:

- Které atribut prvky programu může použít pro. Pokud omezíte její používání, atribut lze použít na jakýkoli z následujících prvků programu:
  - sestavení
  - module
  - pole
  - event
  - – metoda
  - Param
  - property
  - return
  - – typ
- Určuje, zda atribut lze použít na jednom elementu programu několikrát.
- Určuje, zda atributy jsou zděděny z odvozených tříd.

Výchozí nastavení vypadat jako v následujícím příkladu, při použití explicitně:

[!code-csharp[Define a new attribute](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#1)]

V tomto příkladu `NewAttribute` třídy lze použít na libovolný prvek programu podporované. Ale lze jej použít pouze jednou pro každou entitu. Atribut je zděděn z odvozené třídy při použití na základní třídu.

<xref:System.AttributeUsageAttribute.AllowMultiple> a <xref:System.AttributeUsageAttribute.Inherited> jsou argumenty nepovinné, tak má stejný účinek následující kód:

[!code-csharp[Omit optional attributes](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#2)]

První <xref:System.AttributeUsageAttribute> argument musí být jeden nebo více prvků <xref:System.AttributeTargets> výčtu. Více typů cíl může být propojený spolu s operátorem OR, stejně jako v následujícím příkladu:

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#1)]

Od C# 7.3, atributy lze použít u vlastnosti nebo pomocné pole automaticky implementované vlastnosti. Pokud nezadáte platí atribut pro vlastnost, `field` specifikátor atributu. Obě jsou uvedeny v následujícím příkladu:

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#2)]

Pokud <xref:System.AttributeUsageAttribute.AllowMultiple> argument je `true`, pak výsledný atribut lze použít více než jednou na jednu entitu, jak je znázorněno v následujícím příkladu:

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/MultiUseAttribute.cs#1)]

V takovém případě `MultiUseAttribute` můžete použít opakovaně, protože `AllowMultiple` je nastavena na `true`. Oba formáty pro použití více atributů jsou platné.

Pokud <xref:System.AttributeUsageAttribute.Inherited> je `false`, pak atribut není zděděn z třídy odvozené z třídy s atributy. Příklad:

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/NonInheritedAttribute.cs#1)]

V tomto případě `NonInheritedAttribute` neplatí pro `DClass` prostřednictvím dědičnosti.

## <a name="remarks"></a>Poznámky

`AttributeUsage` Atribut je jedno použití atributu – jej nelze použít více než jednou pro tutéž třídu. `AttributeUsage` je alias pro <xref:System.AttributeUsageAttribute>.

Další informace najdete v tématu [přístup k atributy podle použití reflexe (C#)](accessing-attributes-by-using-reflection.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje účinek <xref:System.AttributeUsageAttribute.Inherited> a <xref:System.AttributeUsageAttribute.AllowMultiple> argumenty, které mají <xref:System.AttributeUsageAttribute> atribut a jak mohou být uvedené vlastní atributy použité na třídu.

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

## <a name="see-also"></a>Viz také:

- <xref:System.Attribute>
- <xref:System.Reflection>
- [Průvodce programováním v jazyce C#](../..//index.md)
- [Atributy](../../../..//standard/attributes/index.md)
- [Reflexe (C#)](../reflection.md)
- [Atributy](index.md)
- [Vytváření vlastních atributů (C#)](creating-custom-attributes.md)
- [Přístup k atributům pomocí reflexe (C#)](accessing-attributes-by-using-reflection.md)
