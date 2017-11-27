---
title: "Atribut & č. 39; &lt;attributename&gt;& č. 39; nelze použít více než jednou."
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords: BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 216cf54fd164ca95b6378517a679b5b54183559f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="attribute-39ltattributenamegt39-cannot-be-applied-multiple-times"></a>Atribut & č. 39; &lt;attributename&gt;& č. 39; nelze použít více než jednou.
Atribut lze použít pouze jednou. `AttributeUsage` Atribut určuje, zda atribut můžete použít více než jednou.  
  
 **ID chyby:** BC30663  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Ujistěte se, že atribut se použije pouze jednou.  
  
2.  Pokud používáte vlastní atributy, které jste vytvořili, zvažte změnu jejich `AttributeUsage` atribut umožňuje více atributů využití, stejně jako v následujícím příkladu.  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.AttributeUsageAttribute>  
 [Vytváření vlastních atributů](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [AttributeUsage](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
