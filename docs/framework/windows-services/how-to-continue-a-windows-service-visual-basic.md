---
title: 'Postupy: Pokračování služby systému Windows (Visual Basic)'
description: Přečtěte si, jak používat komponentu ServiceController k pokračování služby Windows (například služby Správce služby IIS) na místním počítači s Visual Basic.
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
ms.openlocfilehash: 2a04e330ea7dc37552053b2a7915909c011727f8
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925784"
---
# <a name="how-to-continue-a-windows-service-visual-basic"></a>Postupy: Pokračování služby systému Windows (Visual Basic)
Tento příklad používá <xref:System.ServiceProcess.ServiceController> komponentu k pokračování služby Správce služby IIS v místním počítači.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#13](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#13)]  
  
 Tento příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense. Ve výběru fragmentu kódu je umístěn v **operačním systému Windows > služby systému Windows**. Další informace naleznete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkaz na projekt System.serviceprocess.dll.  
  
- Přístup ke členům <xref:System.ServiceProcess> oboru názvů. Přidejte `Imports` příkaz, pokud ve svém kódu plně nekvalifikujete názvy členů. Další informace naleznete v tématu [příkaz Imports (obor názvů a typ rozhraní .NET)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="robust-programming"></a>Robustní programování  
 <xref:System.ServiceProcess.ServiceController.MachineName%2A>Vlastnost <xref:System.ServiceProcess.ServiceController> třídy je ve výchozím nastavení místní počítač. Chcete-li odkazovat na služby systému Windows na jiném počítači, změňte <xref:System.ServiceProcess.ServiceController.MachineName%2A> vlastnost na název počítače.  
  
 Metodu nelze volat <xref:System.ServiceProcess.ServiceController.Continue%2A> ve službě, dokud není stav řadiče služby <xref:System.ServiceProcess.ServiceControllerStatus.Paused> .  
  
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
