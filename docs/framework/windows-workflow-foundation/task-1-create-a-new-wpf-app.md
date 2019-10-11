---
title: 'Úloha 1: vytvoření nové aplikace Windows Presentation Foundation'
ms.date: 03/30/2017
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
ms.openlocfilehash: 3205840da575041b449eb841fc8084e89937fca7
ms.sourcegitcommit: 10db6551ea3c971470cf5d2cc21ba1cbcefe5c55
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/08/2019
ms.locfileid: "72031892"
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a>Úloha 1: vytvoření nové aplikace Windows Presentation Foundation

V této úloze vytvoříte prázdnou aplikaci Windows Presentation Foundation (WPF) pomocí šablony Visual Studio aplikace WPF a přidáte odkazy na příslušná sestavení pracovního postupu [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)].  
  
## <a name="to-create-the-wpf-application-project"></a>Vytvoření projektu aplikace WPF

1. Otevřete Visual Studio a v nabídce **soubor** přejděte na příkaz **Nový**a klikněte na **projekt**.

2. V dialogovém okně **Nový projekt** vyberte v podokně **Nainstalované šablony** na levé straně pole buď  **C# vizuál** , nebo **Visual Basic** . Pokud se zvolený jazyk nezobrazí, podívejte se do části **jiné jazyky**.

3. V podokně **Nainstalované šablony** vyberte **Windows** .

4. V horním podokně potvrďte, že je v rozevíracím seznamu vybrána možnost (výchozí hodnota) **.NET Framework 4** , a pak vyberte **aplikace WPF**.

5. V dolní části okna nastavte název projektu na **HostingApplication** .

6. Nastavte název řešení na **RehostingTheDesigner**.

7. Kliknutím na tlačítko **OK** vytvořte projekt aplikace. Visual Studio vytvoří základní uživatelské rozhraní WPF pro vaši aplikaci a zahrne příslušné soubory XAML a kódu na pozadí.

8. Přidejte odkazy na **WorkflowModel** sestavení. To provedete tak, že v **Průzkumník řešení**kliknete pravým tlačítkem na projekt **HostingApplication** a vyberete **Přidat odkaz**.

9. V dialogovém okně **Přidat odkaz** klikněte na kartu **.NET** , podržte stisknutou klávesu CTRL, vyberte následující sestavení a klikněte na tlačítko **OK**:

    - System. Activities
    - System. Activities. Presentation
    - System. Activities. Core. Presentation

10. Další informace o tom, jak hostovat plátno návrhu návrháře pracovních postupů, najdete v tématu [Úloha 2: hostování Návrhář postupu provádění](task-2-host-the-workflow-designer.md) .

## <a name="see-also"></a>Viz také:

- [Změna hostování Návrháře postupu provádění](rehosting-the-workflow-designer.md)
- [Úkol 2: Hostování Návrháře postupu provádění](task-2-host-the-workflow-designer.md)
