---
title: 'Postupy: Pokračování služby systému Windows (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
f1_keywords:
- ServiceController.Continue
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: e5d13760-4c83-4b0d-abef-39852677cd7a
author: ghogen
ms.openlocfilehash: 255dccfb74eced63ffbeff7ef567083a504cc6da
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47108368"
---
# <a name="how-to-continue-a-windows-service-visual-basic"></a>Postupy: Pokračování služby systému Windows (Visual Basic)
V tomto příkladu <xref:System.ServiceProcess.ServiceController> komponenty pokračujte služba správy služby IIS v místním počítači.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#13](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#13)]  
  
 Tento příklad kódu je také dostupný jako fragment kódu technologie IntelliSense. V dialogu pro výběr fragmentu kódu je umístěn v **operačního systému Windows > služby Windows**. Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkaz na projekt do System.serviceprocess.dll.  
  
-   Přístup k členům <xref:System.ServiceProcess> oboru názvů. Přidat `Imports` příkazu, pokud jste nejsou kvalifikaci plně názvy členů ve vašem kódu. Další informace najdete v tématu [příkaz Imports (Namespace .NET a typ)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="robust-programming"></a>Robustní programování  
 <xref:System.ServiceProcess.ServiceController.MachineName%2A> Vlastnost <xref:System.ServiceProcess.ServiceController> místního počítače ve výchozím nastavení je třída. Chcete-li odkazovat služeb Windows na jiný počítač, změňte <xref:System.ServiceProcess.ServiceController.MachineName%2A> nastavte název tohoto počítače.  
  
 Nelze volat <xref:System.ServiceProcess.ServiceController.Continue%2A> metodu na služby, dokud je stav služby řadiče <xref:System.ServiceProcess.ServiceControllerStatus.Paused>.  
  
 Následující podmínky mohou způsobit výjimku:  
  
-   Službu nelze obnovit. (<xref:System.InvalidOperationException>)  
  
-   Došlo k chybě při přístupu k systému rozhraní API. (<xref:System.ComponentModel.Win32Exception>)  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Řízení služeb v počítači může být omezena pomocí <xref:System.ServiceProcess.ServiceControllerPermissionAccess> nastavení oprávnění ve výčtu <xref:System.ServiceProcess.ServiceControllerPermission> třídy.  
  
 Přístup k informacím o služby může být omezena pomocí <xref:System.Security.Permissions.PermissionState> nastavení oprávnění ve výčtu <xref:System.Security.Permissions.SecurityPermission> třídy.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceProcess.ServiceController>  
 <xref:System.ServiceProcess.ServiceControllerStatus>  
 [Postupy: Pozastavení služby systému Windows (Visual Basic)](../../../docs/framework/windows-services/how-to-pause-a-windows-service-visual-basic.md)
