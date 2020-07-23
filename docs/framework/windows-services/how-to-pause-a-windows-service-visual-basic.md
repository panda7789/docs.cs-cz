---
title: 'Postupy: Pozastavení služby systému Windows (Visual Basic)'
description: Přečtěte si, jak pomocí komponenty ServiceController pozastavit službu systému Windows (například službu Správce služby IIS) na místním počítači s Visual Basic.
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
ms.openlocfilehash: 628cc2e896f7f8a289e52674b721c4aef605854c
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925563"
---
# <a name="how-to-pause-a-windows-service-visual-basic"></a>Postupy: Pozastavení služby systému Windows (Visual Basic)
Tento příklad používá <xref:System.ServiceProcess.ServiceController> komponentu k pozastavení služby Správce služby IIS v místním počítači.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 Tento příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense. Ve výběru fragmentu kódu je umístěn v **operačním systému Windows > služby systému Windows**. Další informace naleznete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkaz na projekt System.serviceprocess.dll.  
  
- Přístup ke členům <xref:System.ServiceProcess> oboru názvů. Přidejte `Imports` příkaz, pokud ve svém kódu plně nekvalifikujete názvy členů. Další informace naleznete v tématu [příkaz Imports (obor názvů a typ rozhraní .NET)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="robust-programming"></a>Robustní programování  
 <xref:System.ServiceProcess.ServiceController.MachineName%2A>Vlastnost <xref:System.ServiceProcess.ServiceController> třídy je ve výchozím nastavení místní počítač. Chcete-li odkazovat na služby systému Windows na jiném počítači, změňte <xref:System.ServiceProcess.ServiceController.MachineName%2A> vlastnost na název počítače.  
  
 Následující podmínky mohou způsobit výjimku:  
  
- Službu nelze pozastavit. (<xref:System.InvalidOperationException>)  
  
- Při přístupu k rozhraní API systému došlo k chybě. (<xref:System.ComponentModel.Win32Exception>)  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Řízení služeb v počítači může být omezeno pomocí nástroje <xref:System.ServiceProcess.ServiceControllerPermissionAccess> k nastavení oprávnění v nástroji <xref:System.ServiceProcess.ServiceControllerPermission> .  
  
 Přístup k informacím o službě může být omezen použitím sady <xref:System.Security.Permissions.PermissionState> k nastavení oprávnění v nástroji <xref:System.Security.Permissions.SecurityPermission> .  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>
- [Postupy: Pokračování služby systému Windows (Visual Basic)](how-to-continue-a-windows-service-visual-basic.md)
