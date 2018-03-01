---
title: "Postupy: Zápis zpráv protokolu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Application.Log object, writing log messags
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ae4d875fd4f95ca51fff565551009e780b17d07a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-log-messages-visual-basic"></a>Postupy: Zápis zpráv protokolu (Visual Basic)
Můžete použít `My.Application.Log` a `My.Log` objekty do protokolu informace o vaší aplikaci. Tento příklad ukazuje způsob použití `My.Application.Log.WriteEntry` metoda do protokolu informace o trasování.  
  
 K protokolování informací o výjimce, použijte `My.Application.Log.WriteException` metoda; viz [postup: výjimky protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `My.Application.Log.WriteEntry` metoda k zapsání informací o trasování.  
  
 [!code-vb[VbVbalrMyApplicationLog#11](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-write-log-messages_1.vb)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Ujistěte se, že data, která se zapisují do protokolu neobsahuje citlivé informace, jako jsou hesla uživatele. Další informace najdete v tématu [práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [Práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [Postupy: protokolování výjimek](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)  
 [Návod: Zjištění, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)  
 [Návod: Změna místa, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)  
 [Návod: Filtrování výstupu My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)
