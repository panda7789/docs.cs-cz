---
title: Atribut '<attribute>' nelze použít, protože formát čísla GUID '<number>' není správný.
ms.date: 07/20/2015
f1_keywords:
- vbc32500
- bc32500
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
ms.openlocfilehash: 554c38c8f44999feba4cfa04d58ce2f07e955eb1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409917"
---
# <a name="attribute-cannot-be-applied-because-the-format-of-the-guid-number-is-not-correct"></a>Atribut '\<attribute>' nelze použít, protože formát čísla GUID '\<number>' není správný.

`COMClassAttribute`Blok atributu Určuje globálně jedinečný identifikátor (GUID), který nevyhovuje správnému formátu identifikátoru GUID. `COMClassAttribute`používá identifikátory GUID k jednoznačné identifikaci třídy, rozhraní a události vytvoření.  
  
 Identifikátor GUID se skládá z 16 bajtů, z nichž první osm jsou číslice a poslední osm jsou binární. Vygeneruje se pomocí nástrojů Microsoftu, jako je Uuidgen. exe, a zaručuje, že budou jedinečné v prostoru a v čase.  
  
 **ID chyby:** BC32500  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Určete správný identifikátor GUID nebo identifikátory GUID, které jsou nezbytné k identifikaci objektu COM.  
  
2. Zajistěte, aby byly řetězce GUID prezentované `COMClassAttribute` bloku atributu správně zkopírovány.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Guid>
- [Přehled atributů](../../programming-guide/concepts/attributes/index.md)
