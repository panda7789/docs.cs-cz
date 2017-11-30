---
title: Vstup za koncem souboru
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 27de462d5d28ee09107d75afe8269e7401c4dc39
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="input-past-end-of-file"></a>Vstup za koncem souboru
Buď `Input` příkaz je čtení ze souboru, který je prázdný nebo ve které se používá všechna data, nebo jste použili `EOF` funkce souborem otevřen pro binární.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Použití `EOF` funkce bezprostředně před `Input` příkaz pro zjištění konec souboru.  
  
2.  Pokud soubor je otevřen pro binární, použijte `Seek` a `Loc`.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.FileSystem.Input%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>
