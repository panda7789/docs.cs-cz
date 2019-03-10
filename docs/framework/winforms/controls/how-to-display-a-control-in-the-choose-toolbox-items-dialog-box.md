---
title: 'Postupy: Zobrazení ovládacího prvku v zvolit položky panelu nástrojů – dialogové okno'
ms.date: 03/30/2017
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
ms.openlocfilehash: 191a0848d01eb043420866052b64e2284eb92b49
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720131"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a>Postupy: Zobrazení ovládacího prvku v zvolit položky panelu nástrojů – dialogové okno
Vytvořte a rozdistribuujte ovládací prvky, možná budete chtít tyto ovládací prvky se zobrazí v **zvolit položky nástrojů** dialogové okno, které se zobrazí, když kliknete pravým tlačítkem myši **nástrojů** a vyberte  **Výběr položek**. Můžete povolit ovládacího prvku se zobrazí v tomto dialogovém AssemblyFoldersEx postupem registrace.  
  
### <a name="to-display-your-control-in-the-choose-toolbox-items-dialog-box"></a>Chcete-li zobrazit ovládací prvek v dialogovém okně Zvolit položky nástrojů  
  
-   Nainstalujte sestavení ovládacího prvku do globální mezipaměti sestavení. Další informace najdete v tématu [jak: Instalace sestavení do globální mezipaměti sestavení](../../app-domains/how-to-install-an-assembly-into-the-gac.md)  
  
     -nebo-  
  
-   Zaregistrujte ovládací prvek a jeho přidružené sestavení doby návrhu AssemblyFoldersEx postupem registrace. AssemblyFoldersEx je umístění registru, kam dodavateli z jiných ukládat cesty pro každou verzi rozhraní framework, která podporují. Doby návrhu řešení se můžete podívat v tomto umístění v registru najít referenční sestavení. Skript registru můžete zadat ovládací prvky, které chcete zobrazit na panelu nástrojů. Další informace najdete v tématu [nasazení vlastní ovládací prvek a sestavení doby návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee849818(v=vs.100)).  
  
## <a name="see-also"></a>Viz také:
- [Zvolte dialogové okno položky panelu nástrojů (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))
- [Nasazení vlastního ovládacího prvku a sestavení doby návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee849818(v=vs.100))
- [Vývoj ovládacích prvků Windows Forms v době návrhu](developing-windows-forms-controls-at-design-time.md)
- [Postupy: Instalace sestavení do globální mezipaměti sestavení](../../app-domains/how-to-install-an-assembly-into-the-gac.md)
- [Návod: Automatické vyplnění nástrojů vlastními komponentami](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
