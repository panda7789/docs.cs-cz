---
title: Atribut '<attribute>' nelze použít, protože formát čísla GUID '<number>' není správný.
ms.date: 07/20/2015
f1_keywords:
- vbc32500
- bc32500
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
ms.openlocfilehash: f7b6e42480075666ce9f7e8fc6966bd4bb6b888a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73977319"
---
# <a name="attribute-cannot-be-applied-because-the-format-of-the-guid-number-is-not-correct"></a>atribut\<atributu > nelze použít, protože formát identifikátoru GUID\<číslo > není správný.

`COMClassAttribute` blok atributu Určuje globálně jedinečný identifikátor (GUID), který nevyhovuje správnému formátu identifikátoru GUID. `COMClassAttribute` používá identifikátory GUID k jednoznačné identifikaci třídy, rozhraní a události vytvoření.  
  
 Identifikátor GUID se skládá z 16 bajtů, z nichž první osm jsou číslice a poslední osm jsou binární. Vygeneruje se pomocí nástrojů Microsoftu, jako je Uuidgen. exe, a zaručuje, že budou jedinečné v prostoru a v čase.  
  
 **ID chyby:** BC32500  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Určete správný identifikátor GUID nebo identifikátory GUID, které jsou nezbytné k identifikaci objektu COM.  
  
2. Zajistěte, aby byly správně zkopírovány řetězce GUID prezentované do bloku atributu `COMClassAttribute`.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Guid>
- [Přehled atributů](../../../visual-basic/programming-guide/concepts/attributes/index.md)
