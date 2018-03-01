---
title: "& č. 39; &lt;atribut&gt;& č. 39; nelze použít, protože formát identifikátoru GUID & č. 39;&lt; číslo&gt;& č. 39; není správný"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32500
- bc32500
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8ead07d12064dbe18a1e23d4d1343b1efba1b533
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="39ltattributegt39-cannot-be-applied-because-the-format-of-the-guid-39ltnumbergt39-is-not-correct"></a>& č. 39; &lt;atribut&gt;& č. 39; nelze použít, protože formát identifikátoru GUID & č. 39;&lt; číslo&gt;& č. 39; není správný
A `COMClassAttribute` bloku atribut Určuje globálně jedinečný identifikátor (GUID), který není v souladu s správný formát pro identifikátor GUID. `COMClassAttribute`identifikátory GUID používá k jedinečné identifikaci třídu rozhraní a vytvoření události.  
  
 Identifikátor GUID se skládá z 16 bajtů, které první osm jsou číselné a poslední osm jsou binární. Při generování pomocí nástroje Microsoft, jako je například uuidgen.exe a je musí být jedinečný v místa a času.  
  
 **ID chyby:** BC32500  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Určete správný identifikátor GUID nebo identifikátory GUID, které jsou nezbytné k identifikaci objektu COM.  
  
2.  Ujistěte se, řetězce GUID sdělit k `COMClassAttribute` správně zkopírované atribut bloku.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Guid>  
[Přehled atributy](../../../visual-basic/programming-guide/concepts/attributes/index.md)

