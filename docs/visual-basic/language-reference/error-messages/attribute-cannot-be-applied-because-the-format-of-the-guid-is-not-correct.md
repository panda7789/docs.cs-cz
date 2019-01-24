---
title: '&#39;&lt;atribut&gt; &#39; nelze použít, protože formát čísla GUID &#39; &lt;číslo&gt; &#39; není správná'
ms.date: 07/20/2015
f1_keywords:
- vbc32500
- bc32500
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
ms.openlocfilehash: 85b8c9dcccbb307d8a744e33a5f1d4b1775fda04
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623661"
---
# <a name="39ltattributegt39-cannot-be-applied-because-the-format-of-the-guid-39ltnumbergt39-is-not-correct"></a>&#39;&lt;atribut&gt; &#39; nelze použít, protože formát čísla GUID &#39; &lt;číslo&gt; &#39; není správná
A `COMClassAttribute` bloku atributu Určuje globálně jedinečný identifikátor (GUID), který není v souladu s správný formát pro identifikátor GUID. `COMClassAttribute` identifikátory GUID k jednoznačné identifikaci třídy, rozhraní a vytvoření události.  
  
 Identifikátor GUID se skládá z 16 bajtů, z nichž první osm jsou číselná a posledních osm jsou binární. Je vygenerován pomocí nástroje Microsoft, jako jsou uuidgen.exe a je zaručeně jedinečná v místa a času.  
  
 **ID chyby:** BC32500  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Určete správný identifikátor GUID nebo identifikátory GUID, které jsou nezbytné k identifikaci objektu modelu COM.  
  
2.  Ujistěte se, že řetězce GUID uvedené na `COMClassAttribute` bloku atributu se zkopíroval správně.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Guid>
- [Přehled atributy](../../../visual-basic/programming-guide/concepts/attributes/index.md)

