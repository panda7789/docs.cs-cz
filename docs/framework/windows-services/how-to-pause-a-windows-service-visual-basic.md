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
ms.openlocfilehash: 20bc177ccf2646f79994553803568531233ea5c4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935487"
---
# <a name="how-to-pause-a-windows-service-visual-basic"></a>Postupy: Pozastavení služby systému Windows (Visual Basic)
Tento příklad používá <xref:System.ServiceProcess.ServiceController> komponentu k pozastavení služby Správce služby IIS v místním počítači.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 Tento příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense. Ve výběru fragmentu kódu je umístěn v **operačním systému Windows > služby systému Windows**. Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkaz na projekt System. ServiceProcess. dll.  
  
- Přístup ke členům <xref:System.ServiceProcess> oboru názvů. `Imports` Přidejte příkaz, pokud ve svém kódu plně nekvalifikujete názvy členů. Další informace naleznete v tématu [příkaz Imports (obor názvů a typ rozhraní .NET)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="robust-programming"></a>Robustní programování  
 <xref:System.ServiceProcess.ServiceController.MachineName%2A> Vlastnost<xref:System.ServiceProcess.ServiceController> třídy je ve výchozím nastavení místní počítač. Chcete-li odkazovat na služby systému Windows na jiném <xref:System.ServiceProcess.ServiceController.MachineName%2A> počítači, změňte vlastnost na název počítače.  
  
 Následující podmínky mohou způsobit výjimku:  
  
- Službu nelze pozastavit. (<xref:System.InvalidOperationException>)  
  
- Při přístupu k rozhraní API systému došlo k chybě. (<xref:System.ComponentModel.Win32Exception>)  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Řízení služeb v počítači může být omezeno pomocí nástroje <xref:System.ServiceProcess.ServiceControllerPermissionAccess> k nastavení oprávnění <xref:System.ServiceProcess.ServiceControllerPermission>v nástroji.  
  
 Přístup k informacím o službě může být omezen použitím sady <xref:System.Security.Permissions.PermissionState> k nastavení oprávnění <xref:System.Security.Permissions.SecurityPermission>v nástroji.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>
- [Postupy: Pokračování služby systému Windows (Visual Basic)](../../../docs/framework/windows-services/how-to-continue-a-windows-service-visual-basic.md)
