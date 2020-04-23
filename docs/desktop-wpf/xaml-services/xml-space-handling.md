---
title: Práce s atributem xml:space v jazyce XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: 886f906b6d1e3a10920dbf52e36bf76324c5a9f2
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071435"
---
# <a name="xmlspace-handling-in-xaml"></a>Práce s atributem xml:space v jazyce XAML

Atribut `xml:space` je atribut definovaný jazykem XML, který deklaruje významné chování zpracování prázdného místa v rámci elementu objektu. Toto chování je relevantní pro veškerý obsah (vnitřní `xml:space` text) obsažené v elementu, kde je deklarována a také obory podřízených prvků.

## <a name="xaml-attribute-usage"></a>Použití atributu XAML

```xaml
<object xml:space="preserve" />
```

 \-nebo -

```xaml
<object xml:space="default" />
```

## <a name="remarks"></a>Poznámky

Definice atributu `xml:space` v XAML včetně jeho dvou možných hodnot je odvozena od `xml:space` definovaného jako "speciální atribut" specifikacemi W3C pro XML.

Výchozí hodnota atributu `xml:space` je hodnota `"default"`literálu . Pro hodnotu `"default"`, `xml:space` nebo pokud není uvedeno vůbec, chování významné prázdné místo analýzy je výchozí zpracování, jak je definováno v tématu [zpracování prázdnémísto v XAML](white-space-processing.md).

Chcete-li zachovat prázdné místo `xml:space="preserve"` v obsahu prvku objektu, zadejte na tomto prvku objektu.

Při většině interpretací `xml:space` jsou efekty atributů a hodnota atributu vymezeny na podřízené prvky.

Úplnou diskusi o zpracování prázdného místa v XAML naleznete [v tématu Zpracování prázdného místa v XAML](white-space-processing.md).

## <a name="see-also"></a>Viz také

- [Zpracování prázdných znaků v jazyku XAML](white-space-processing.md)
- [Přehled XAML (WPF)](../fundamentals/xaml.md)
