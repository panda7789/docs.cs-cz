---
title: 'Postupy: Pozastavení služby systému Windows (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
f1_keywords:
- ServiceController.Pause
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: eddb9409-942b-46b6-a2ce-fbd4c65f2790
author: ghogen
ms.openlocfilehash: 8a75c6a03f130e0a141107c81c946fc6a33b9f6c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592540"
---
# <a name="how-to-pause-a-windows-service-visual-basic"></a>Postupy: Pozastavení služby systému Windows (Visual Basic)
V tomto příkladu <xref:System.ServiceProcess.ServiceController> součásti pozastavit služba správy služby IIS v místním počítači.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 Tento příklad kódu je také dostupný jako fragment kódu technologie IntelliSense. V dialogu pro výběr fragmentu kódu je umístěn v **operačního systému Windows > služby Windows**. Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkaz na projekt do System.serviceprocess.dll.  
  
- Přístup k členům <xref:System.ServiceProcess> oboru názvů. Přidat `Imports` příkazu, pokud jste nejsou kvalifikaci plně názvy členů ve vašem kódu. Další informace najdete v tématu [příkaz Imports (Namespace .NET a typ)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="robust-programming"></a>Robustní programování  
 <xref:System.ServiceProcess.ServiceController.MachineName%2A> Vlastnost <xref:System.ServiceProcess.ServiceController> místního počítače ve výchozím nastavení je třída. Chcete-li odkazovat služeb Windows na jiný počítač, změňte <xref:System.ServiceProcess.ServiceController.MachineName%2A> nastavte název tohoto počítače.  
  
 Následující podmínky mohou způsobit výjimku:  
  
- Službu nelze pozastavit. (<xref:System.InvalidOperationException>)  
  
- Došlo k chybě při přístupu k systému rozhraní API. (<xref:System.ComponentModel.Win32Exception>)  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Řízení služeb v počítači může být omezena pomocí <xref:System.ServiceProcess.ServiceControllerPermissionAccess> nastavení oprávnění ve <xref:System.ServiceProcess.ServiceControllerPermission>.  
  
 Přístup k informacím o služby může být omezena pomocí <xref:System.Security.Permissions.PermissionState> nastavení oprávnění ve <xref:System.Security.Permissions.SecurityPermission>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>
- [Postupy: Pokračování služby Windows (Visual Basic)](../../../docs/framework/windows-services/how-to-continue-a-windows-service-visual-basic.md)
