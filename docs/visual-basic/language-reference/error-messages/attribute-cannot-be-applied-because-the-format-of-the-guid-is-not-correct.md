---
title: Atribut '<attribute>' nelze použít, protože formát čísla GUID '<number>' není správný.
ms.date: 07/20/2015
f1_keywords:
- vbc32500
- bc32500
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
ms.openlocfilehash: ab821db45ae834e82aa134b6f20ded14d43709ef
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832265"
---
# <a name="attribute-cannot-be-applied-because-the-format-of-the-guid-number-is-not-correct"></a>"\<atribut >' nelze použít, protože formát čísla GUID '\<číslo >' není správná
A `COMClassAttribute` bloku atributu Určuje globálně jedinečný identifikátor (GUID), který není v souladu s správný formát pro identifikátor GUID. `COMClassAttribute` identifikátory GUID k jednoznačné identifikaci třídy, rozhraní a vytvoření události.  
  
 Identifikátor GUID se skládá z 16 bajtů, z nichž první osm jsou číselná a posledních osm jsou binární. Je vygenerován pomocí nástroje Microsoft, jako jsou uuidgen.exe a je zaručeně jedinečná v místa a času.  
  
 **ID chyby:** BC32500  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Určete správný identifikátor GUID nebo identifikátory GUID, které jsou nezbytné k identifikaci objektu modelu COM.  
  
2.  Ujistěte se, že řetězce GUID uvedené na `COMClassAttribute` bloku atributu se zkopíroval správně.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Guid>
- [Přehled atributy](../../../visual-basic/programming-guide/concepts/attributes/index.md)
