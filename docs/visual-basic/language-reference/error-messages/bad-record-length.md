---
title: Chybná délka záznamu
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID59
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 747d62cb41ef841b4486e0c7108c37a86929683e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="bad-record-length"></a>Chybná délka záznamu
Mezi možné příčiny této chyby patří:  
  
-   Délka zadaná v proměnné záznam `FileGet`, `FileGetObject`, `FilePut` nebo `FilePutObject` příkazu se liší od délka zadaná v odpovídající `FileOpen` příkaz.  
  
-   Proměnné v `FilePut` nebo `FilePutObject` příkaz není nebo obsahuje řetězec s proměnnou délkou.  
  
-   Proměnné v `FilePut` nebo `FilePutObject` zahrnuje nebo je `Variant` typu.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zajistěte, aby součet hodnot velikosti pevnou délkou proměnné v uživatelsky definovaný typ. typ záznamu proměnnou definujete je stejný jako hodnota uvedená v `FileOpen` na příkaz `Len` klauzule.  
  
2.  Pokud proměnné v `FilePut` nebo `FilePutObject` příkaz nebo obsahuje řetězec s proměnnou délkou, zkontrolujte, zda řetězec proměnné délky je kratší než délka záznamu zadaný v aspoň 2 znaky `Len` klauzuli `FileOpen` příkaz.  
  
3.  Pokud proměnné v `FilePut` nebo `FilePutObject` zahrnuje nebo je `Variant` zkontrolujte, zda řetězec proměnné délky je kratší než délka záznamu zadaný v minimálně 4 bajtů `Len` klauzuli `FileOpen` příkaz.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>
