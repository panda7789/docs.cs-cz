---
title: 'Postupy: Zápis zpráv protokolu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, writing log messages
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
ms.openlocfilehash: 007d08917ed5ecae6889d03d820d48e4695c9344
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57676119"
---
# <a name="how-to-write-log-messages-visual-basic"></a>Postupy: Zápis zpráv protokolu (Visual Basic)

Můžete použít `My.Application.Log` a `My.Log` objekty k protokolování informací o vaší aplikaci. Tento příklad ukazuje způsob použití `My.Application.Log.WriteEntry` metody do protokolu informace o trasování.

Protokolování informací o výjimce, použijte `My.Application.Log.WriteException` metoda; viz [jak: Protokolování výjimek](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).

## <a name="example"></a>Příklad

V tomto příkladu `My.Application.Log.WriteEntry` metody zapsat informace trasování.

[!code-vb[VbVbalrMyApplicationLog#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#11)]

## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework

Ujistěte se, že data, která se zaznamená do protokolu neobsahuje citlivé informace, jako jsou hesla uživatele. Další informace najdete v tématu [práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Postupy: Výjimky protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [Návod: Určení, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [Návod: Změna, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [Návod: Filtrování výstupu My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)
