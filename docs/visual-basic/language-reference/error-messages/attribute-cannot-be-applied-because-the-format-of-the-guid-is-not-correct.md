---
title: '&#39;&lt;atribut&gt; &#39; nelze použít, protože formát identifikátoru GUID &#39; &lt;číslo&gt; &#39; není správný'
ms.date: 07/20/2015
f1_keywords:
- vbc32500
- bc32500
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
ms.openlocfilehash: 93b208b2119942f939a3af223c2f562c6097f7a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="39ltattributegt39-cannot-be-applied-because-the-format-of-the-guid-39ltnumbergt39-is-not-correct"></a>&#39;&lt;atribut&gt; &#39; nelze použít, protože formát identifikátoru GUID &#39; &lt;číslo&gt; &#39; není správný
A `COMClassAttribute` bloku atribut Určuje globálně jedinečný identifikátor (GUID), který není v souladu s správný formát pro identifikátor GUID. `COMClassAttribute` identifikátory GUID používá k jedinečné identifikaci třídu rozhraní a vytvoření události.  
  
 Identifikátor GUID se skládá z 16 bajtů, které první osm jsou číselné a poslední osm jsou binární. Při generování pomocí nástroje Microsoft, jako je například uuidgen.exe a je musí být jedinečný v místa a času.  
  
 **ID chyby:** BC32500  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Určete správný identifikátor GUID nebo identifikátory GUID, které jsou nezbytné k identifikaci objektu COM.  
  
2.  Ujistěte se, řetězce GUID sdělit k `COMClassAttribute` správně zkopírované atribut bloku.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Guid>  
[Přehled atributy](../../../visual-basic/programming-guide/concepts/attributes/index.md)

