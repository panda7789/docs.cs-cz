---
title: 'Postupy: Zápis zpráv protokolu'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, writing log messages
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
ms.openlocfilehash: 28c5fe77e2711dfcac96e621a90fb9506eb74775
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410046"
---
# <a name="how-to-write-log-messages-visual-basic"></a>Postupy: Zápis zpráv protokolu (Visual Basic)

Pomocí `My.Application.Log` objektů a můžete `My.Log` protokolovat informace o vaší aplikaci. Tento příklad ukazuje, jak použít `My.Application.Log.WriteEntry` metodu k protokolování informací o trasování.

Pro protokolování informací o výjimce použijte `My.Application.Log.WriteException` metodu; viz [How to: log Exceptions](how-to-log-exceptions.md).

## <a name="example"></a>Příklad

Tento příklad používá `My.Application.Log.WriteEntry` metodu k vypsání informací o trasování.

[!code-vb[VbVbalrMyApplicationLog#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#11)]

## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework

Ujistěte se, že data, která do protokolu zapisujete, neobsahují citlivé informace, jako jsou uživatelská hesla. Další informace najdete v tématu [práce s protokoly aplikací](working-with-application-logs.md).

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Práce s protokoly aplikací](working-with-application-logs.md)
- [Postupy: Protokolování výjimek](how-to-log-exceptions.md)
- [Návod: Zjištění, kam objekt My.Application.Log zapisuje informace](walkthrough-determining-where-my-application-log-writes-information.md)
- [Návod: Změna místa, kam objekt My.Application.Log zapisuje informace](walkthrough-changing-where-my-application-log-writes-information.md)
- [Návod: Filtrování výstupu My.Application.Log](walkthrough-filtering-my-application-log-output.md)
