---
title: Nelze odkazovat na &#39; &lt;název&gt; &#39; protože se jedná o člen pole typu hodnota &#39; &lt;název&gt; &#39; třídy &#39; &lt;classname&gt; &#39;obsahující &#39;System.MarshalByRefObject&#39; jako základní třída
ms.date: 07/20/2015
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
ms.openlocfilehash: a6298c3e0f5102397d5cc3f237a186598c6b5ecc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54739294"
---
# <a name="cannot-refer-to-39ltnamegt39-because-it-is-a-member-of-the-value-typed-field-39ltnamegt39-of-class-39ltclassnamegt39-which-has-39systemmarshalbyrefobject39-as-a-base-class"></a>Nelze odkazovat na &#39; &lt;název&gt; &#39; protože se jedná o člen pole typu hodnota &#39; &lt;název&gt; &#39; třídy &#39; &lt;classname&gt; &#39;obsahující &#39;System.MarshalByRefObject&#39; jako základní třída
`System.MarshalByRefObject` Třída umožňuje aplikacím, které podporují vzdálený přístup k objektům přes hranice aplikačních domén. Typy musí dědit z `MarshalByRejectObject` třídy, pokud je typ použít přes hranice aplikačních domén. Stav objektu nesmí být zkopírována, protože členové objektu nejsou použitelné mimo doménu aplikace, ve kterém byly vytvořeny.  
  
 **ID chyby:** BC30310  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zkontrolujte, abyste měli jistotu, že je člen, který se odkazuje na platný odkaz.  
  
2.  Explicitně kvalifikovat člena s `Me` – klíčové slovo.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.MarshalByRefObject>
- [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)
