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
ms.openlocfilehash: a10e05b0460608a9e67ee4527adf80be3d47438e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053642"
---
# <a name="how-to-continue-a-windows-service-visual-basic"></a>Postupy: Pokračování služby systému Windows (Visual Basic)
Tento příklad používá <xref:System.ServiceProcess.ServiceController> komponentu k pokračování služby Správce služby IIS v místním počítači.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#13](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#13)]  
  
 Tento příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense. Ve výběru fragmentu kódu je umístěn v **operačním systému Windows > služby systému Windows**. Další informace naleznete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkaz na projekt System. ServiceProcess. dll.  
  
- Přístup ke členům <xref:System.ServiceProcess> oboru názvů. Přidejte `Imports` příkaz, pokud ve svém kódu plně nekvalifikujete názvy členů. Další informace naleznete v tématu [příkaz Imports (obor názvů a typ rozhraní .NET)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="robust-programming"></a>Robustní programování  
 <xref:System.ServiceProcess.ServiceController.MachineName%2A> Vlastnost <xref:System.ServiceProcess.ServiceController> třídy je ve výchozím nastavení místní počítač. Chcete-li odkazovat na služby systému Windows na jiném <xref:System.ServiceProcess.ServiceController.MachineName%2A> počítači, změňte vlastnost na název počítače.  
  
 <xref:System.ServiceProcess.ServiceController.Continue%2A> Metodu nelze volat ve službě, dokud není <xref:System.ServiceProcess.ServiceControllerStatus.Paused>stav řadiče služby.  
  
 Následující podmínky mohou způsobit výjimku:  
  
- Službu nelze obnovit. (<xref:System.InvalidOperationException>)  
  
- Při přístupu k rozhraní API systému došlo k chybě. (<xref:System.ComponentModel.Win32Exception>)  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Řízení služeb v počítači může být omezeno pomocí <xref:System.ServiceProcess.ServiceControllerPermissionAccess> výčtu k nastavení oprávnění ve <xref:System.ServiceProcess.ServiceControllerPermission> třídě.  
  
 Přístup k informacím o službě může být omezen pomocí <xref:System.Security.Permissions.PermissionState> výčtu k nastavení oprávnění ve <xref:System.Security.Permissions.SecurityPermission> třídě.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- [Postupy: Pozastavení služby systému Windows (Visual Basic)](how-to-pause-a-windows-service-visual-basic.md)
