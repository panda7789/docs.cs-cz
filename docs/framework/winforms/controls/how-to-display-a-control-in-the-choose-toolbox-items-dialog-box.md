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
ms.openlocfilehash: 7e452c3d3be131b891ee26555e3085fc31b04517
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a>Postupy: Zobrazení ovládacího prvku v dialogovém okně Zvolit položky nástrojů
Při vývoji a distribuovat ovládací prvky, můžete se zobrazí v těchto ovládací prvky **výběr položek sady nástrojů** dialogové okno, které se zobrazí, když kliknete pravým tlačítkem na **sada nástrojů** a vyberte  **Zvolte položky**. Ovládací prvek se objeví v tomto dialogovém pomocí postupu registrace AssemblyFoldersEx můžete povolit.  
  
### <a name="to-display-your-control-in-the-choose-toolbox-items-dialog-box"></a>Chcete-li zobrazit vlastního ovládacího prvku v dialogovém okně Zvolit položky nástrojů  
  
-   Instalovat vaše sestavení ovládacího prvku do globální mezipaměti sestavení. Další informace najdete v tématu [postupy: Instalace sestavení do globální mezipaměti sestavení](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
  
     -nebo-  
  
-   Pomocí postupu registrace AssemblyFoldersEx zaregistrujte vlastní ovládací prvek a jeho přidružené sestavení návrhu. AssemblyFoldersEx je registru umístění, kam jiných dodavatelů ukládat cesty pro každou verzi rozhraní, které podporují. Návrh řešení můžete hledat v tomto umístění registru najít referenční sestavení. Skript registru můžete zadat ovládací prvky, které se má zobrazit v panelu nástrojů. Další informace najdete v tématu [nasazení vlastní ovládací prvek a návrhu sestavení (Visual Studio 2013)](http://msdn.microsoft.com/library/96158eb0-b691-4ae1-9e7b-3c65a1b798cb).  
  
## <a name="see-also"></a>Viz také  
 [Výběr dialogové okno položek sady nástrojů (Visual Studio)](http://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb)  
 [Nasazení vlastního ovládacího prvku a návrhu sestavení (Visual Studio 2013)](http://msdn.microsoft.com/library/96158eb0-b691-4ae1-9e7b-3c65a1b798cb)  
 [Vývoj ovládacích prvků Windows Forms v době návrhu](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [Postupy: Instalace sestavení do globální mezipaměti sestavení](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 [Návod: Automatické vyplnění sady nástrojů vlastními komponentami](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
