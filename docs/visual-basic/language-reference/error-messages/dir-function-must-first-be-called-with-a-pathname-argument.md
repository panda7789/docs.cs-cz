---
title: '&#39;Příkaz dir&#39; funkce musí být nejdříve volána s &#39;cesta&#39; argument'
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: f7e9ef9cc6309f24ae9f8963e910b41180c029b7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54518485"
---
# <a name="39dir39-function-must-first-be-called-with-a-39pathname39-argument"></a>&#39;Příkaz dir&#39; funkce musí být nejdříve volána s &#39;cesta&#39; argument
Počáteční volání `Dir` funkce nezahrnuje `PathName` argument. První volání `Dir` musí obsahovat `PathName`, ale následné volání `Dir` není potřeba zahrnovat parametry se mají načíst další položky.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zadat `PathName` argument ve volání funkce.  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
