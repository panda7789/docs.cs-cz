---
title: "& č. 39; Dir & č. 39; funkce musí být nejdříve volána s a & č. 39; Název cesty & č. 39; argument"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 843918fe9cb0b9dece076b5dc1373c3571588caa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="39dir39-function-must-first-be-called-with-a-39pathname39-argument"></a>& č. 39; Dir & č. 39; funkce musí být nejdříve volána s a & č. 39; Název cesty & č. 39; argument
Počáteční volání `Dir` funkce nezahrnuje `PathName` argument. První volání `Dir` musí obsahovat `PathName`, ale následující volání `Dir` nemusí obsahovat parametry pro načtení další položky.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zadejte `PathName` argument ve volání funkce.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
