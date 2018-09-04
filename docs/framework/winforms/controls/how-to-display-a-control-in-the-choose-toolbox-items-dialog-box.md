---
title: 'Postupy: Zobrazení ovládacího prvku v dialogovém okně Zvolit položky nástrojů'
ms.date: 03/30/2017
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
ms.openlocfilehash: fdda72d60b0f18e76b03e9b7f05060a09763a3f7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43527620"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a>Postupy: Zobrazení ovládacího prvku v dialogovém okně Zvolit položky nástrojů
Vytvořte a rozdistribuujte ovládací prvky, možná budete chtít tyto ovládací prvky se zobrazí v **zvolit položky nástrojů** dialogové okno, které se zobrazí, když kliknete pravým tlačítkem myši **nástrojů** a vyberte  **Výběr položek**. Můžete povolit ovládacího prvku se zobrazí v tomto dialogovém AssemblyFoldersEx postupem registrace.  
  
### <a name="to-display-your-control-in-the-choose-toolbox-items-dialog-box"></a>Chcete-li zobrazit ovládací prvek v dialogovém okně Zvolit položky nástrojů  
  
-   Nainstalujte sestavení ovládacího prvku do globální mezipaměti sestavení. Další informace najdete v tématu [postupy: Instalace sestavení do globální mezipaměti sestavení](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
  
     -nebo-  
  
-   Zaregistrujte ovládací prvek a jeho přidružené sestavení doby návrhu AssemblyFoldersEx postupem registrace. AssemblyFoldersEx je umístění registru, kam dodavateli z jiných ukládat cesty pro každou verzi rozhraní framework, která podporují. Doby návrhu řešení se můžete podívat v tomto umístění v registru najít referenční sestavení. Skript registru můžete zadat ovládací prvky, které chcete zobrazit na panelu nástrojů. Další informace najdete v tématu [nasazení vlastní ovládací prvek a návrhových sestavení (Visual Studio 2013)](https://msdn.microsoft.com/library/96158eb0-b691-4ae1-9e7b-3c65a1b798cb).  
  
## <a name="see-also"></a>Viz také  
 [Zvolte dialogové okno položky panelu nástrojů (Visual Studio)](https://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb)  
 [Nasazení vlastního ovládacího prvku a návrhových sestavení (Visual Studio 2013)](https://msdn.microsoft.com/library/96158eb0-b691-4ae1-9e7b-3c65a1b798cb)  
 [Vývoj ovládacích prvků Windows Forms v době návrhu](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [Postupy: Instalace sestavení do globální mezipaměti sestavení](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 [Návod: Automatické vyplnění sady nástrojů vlastními komponentami](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
