---
title: 'Řešení potíží: Součásti naslouchající protokolům'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
ms.openlocfilehash: dd139935dae7fe4d1334b861e6590df29bab7202
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346859"
---
# <a name="troubleshooting-log-listeners-visual-basic"></a>Řešení potíží: Součásti naslouchající protokolům (Visual Basic)

Pomocí objektů `My.Application.Log` a `My.Log` můžete protokolovat informace o událostech, ke kterým dochází ve vaší aplikaci.  
  
 Chcete-li zjistit, které naslouchací procesy protokolu obdrží tyto zprávy, přečtěte si [Návod: určení, kde my. Application. Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).  
  
 Objekt `Log` může použít filtrování protokolu k omezení množství informací, které protokoluje. Pokud jsou filtry nesprávně nakonfigurované, můžou protokoly obsahovat nesprávné informace. Další informace o filtrování najdete v tématu [Návod: filtrování výstupu my. Application. log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).  
  
 Pokud je ale protokol nesprávně nakonfigurovaný, možná budete potřebovat další informace o jeho aktuální konfiguraci. K těmto informacím se můžete dostat prostřednictvím vlastnosti rozšířené `TraceSource` protokolu.  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a>Určení naslouchacího procesu protokolu pro objekt log v kódu  
  
1. Importujte <xref:System.Diagnostics> obor názvů na začátek souboru kódu. Další informace naleznete v tématu [příkaz Imports (obor názvů a typ rozhraní .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
     [!code-vb[VbVbalrMyApplicationLog#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#13)]  
  
2. Vytvořte funkci, která vrátí řetězec skládající se z informací pro každý naslouchací proces protokolu.  
  
     [!code-vb[VbVbalrMyApplicationLog#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#14)]  
  
3. Předejte kolekci posluchačů trasování protokolu do funkce `GetListeners` a zobrazte návratovou hodnotu.  
  
     [!code-vb[VbVbalrMyApplicationLog#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#19)]  
  
     Další informace najdete v tématu <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Návod: Zjištění, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
