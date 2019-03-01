---
title: 'Postupy: Kontrola stavu připojení v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- Web connections [Visual Basic]
- IsAvailable property [Visual Basic], about IsAvailable
- connections [Visual Basic], checking status
- connection status [Visual Basic]
ms.assetid: 4d9ee8ab-9a6f-4279-ace4-b75afc976a74
ms.openlocfilehash: bb3d5751ae7d88af05c2a77e9b64f9cb28179a35
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973012"
---
# <a name="how-to-check-connection-status-in-visual-basic"></a>Postupy: Kontrola stavu připojení v jazyce Visual Basic
<xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> Vlastnost lze použít k určení, zda má počítač funkční síť a připojení k Internetu.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-check-whether-a-computer-has-a-working-connection"></a>Zkontrolujte, zda počítač má připojení k práci  
  
-   Určení, zda `IsAvailable` vlastnost `True` nebo `False`. Následující kód kontroluje stav vlastnosti a ohlásí ji:  
  
     [!code-vb[VbResourceTasks#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#3)]  
  
     Tento příklad kódu je také dostupný jako fragment kódu technologie IntelliSense. V dialogu pro výběr fragmentu kódu je umístěn v **připojení a sítě**. Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable>
