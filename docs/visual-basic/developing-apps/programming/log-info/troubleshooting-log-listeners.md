---
title: 'Řešení potíží: Součásti naslouchající protokolům'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
ms.openlocfilehash: dd139935dae7fe4d1334b861e6590df29bab7202
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74346859"
---
# <a name="troubleshooting-log-listeners-visual-basic"></a>Řešení potíží: Součásti naslouchající protokolům (Visual Basic)

Objekty `My.Application.Log` a `My.Log` můžete použít k protokolování informací o událostech, ke kterým dochází ve vaší aplikaci.  
  
 Chcete-li zjistit, které posluchače protokolu obdrží tyto zprávy, naleznete [v tématu Návod: Určení, kde my.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).  
  
 Objekt `Log` můžete použít filtrování protokolu omezit množství informací, které protokoluje. Pokud jsou filtry nesprávně nakonfigurovány, protokoly mohou obsahovat nesprávné informace. Další informace o filtrování naleznete v [tématu Návod: Filtrování výstupu my.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).  
  
 Pokud je však protokol nakonfigurován nesprávně, budete pravděpodobně potřebovat další informace o jeho aktuální konfiguraci. K tomuto přístupu se můžete dostat `TraceSource` prostřednictvím rozšířené vlastnosti protokolu.  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a>Určení posluchačů protokolu pro objekt Log v kódu  
  
1. Importujte <xref:System.Diagnostics> obor názvů na začátku souboru kódu. Další informace naleznete [v tématu Imports Statement (Obor názvů.NET a Typ).](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
  
     [!code-vb[VbVbalrMyApplicationLog#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#13)]  
  
2. Vytvořte funkci, která vrací řetězec skládající se z informací pro každý z posluchačů protokolu.  
  
     [!code-vb[VbVbalrMyApplicationLog#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#14)]  
  
3. Předajte kolekci posluchačů trasování `GetListeners` protokolu do funkce a zobrazte vrácenou hodnotu.  
  
     [!code-vb[VbVbalrMyApplicationLog#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#19)]  
  
     Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Práce s protokoly aplikací](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Návod: Zjištění, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
