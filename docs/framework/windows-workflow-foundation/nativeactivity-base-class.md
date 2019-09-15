---
title: Základní třída NativeActivity
ms.date: 03/30/2017
ms.assetid: 254a4c50-425b-426d-a32f-0f7234925bac
ms.openlocfilehash: 604535e39937a75c6d268cf1abbc90dbcd506a16
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989549"
---
# <a name="nativeactivity-base-class"></a>Základní třída NativeActivity

<xref:System.Activities.NativeActivity>je abstraktní třída s chráněným konstruktorem. Podobně <xref:System.Activities.CodeActivity>jako <xref:System.Activities.NativeActivity> , se používá pro psaní <xref:System.Activities.NativeActivity.Execute%2A> imperativního chování implementací metody. Na rozdíl <xref:System.Activities.CodeActivity>od <xref:System.Activities.NativeActivity> , má přístup ke všem vystaveným funkcím modulu runtime pracovního postupu prostřednictvím <xref:System.Activities.NativeActivityContext> objektu předaného <xref:System.Activities.NativeActivity.Execute%2A> metodě.

## <a name="using-nativeactivitycontext"></a>Použití NativeActivityContext
 K funkcím modulu runtime pracovního postupu lze v rámci <xref:System.Activities.NativeActivity.Execute%2A> metody přistupovat pomocí členů `context` parametru typu <xref:System.Activities.NativeActivityContext>. K dispozici <xref:System.Activities.NativeActivityContext> jsou tyto funkce:

- Získání a nastavení argumentů a proměnných.

- Plánování podřízených aktivit pomocí<xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>

- Přerušení provádění aktivity pomocí <xref:System.Activities.NativeActivityContext.Abort%2A>.

- Zrušení podřízeného spuštění pomocí <xref:System.Activities.NativeActivityContext.CancelChild%2A> a <xref:System.Activities.NativeActivityContext.CancelChildren%2A>.

- Přístup k záložekm aktivit pomocí takových <xref:System.Activities.NativeActivityContext.CreateBookmark%2A>metod <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A>jako, <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A>a.

- Vlastní funkce sledování pomocí <xref:System.Activities.CodeActivityContext.Track%2A>.

- Přístup k vlastnostem spuštění aktivity a k vlastnostem hodnoty <xref:System.Activities.CodeActivityContext.GetProperty%2A> pomocí <xref:System.Activities.NativeActivityContext.GetValue%2A>a.

- Plánování akcí a funkcí aktivity pomocí <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> a <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A>.

### <a name="to-create-a-custom-activity-that-inherits-from-nativeactivity"></a>Vytvoření vlastní aktivity, která dědí z NativeActivity

1. OpenVisual Studio 2010.

2. Vyberte **soubor**, **Nový**a pak **projekt**. V okně **typy projektů** vyberte **pracovní postup 4,0** v nabídce  **C# vizuál** a vyberte uzel **v2010** . V okně **šablony** vyberte **Knihovna aktivit** . Pojmenujte nový projekt HelloActivity.

3. Klikněte pravým tlačítkem na Activity1. XAML v projektu HelloActivity a vyberte **Odstranit**.

4. Klikněte pravým tlačítkem myši na projekt HelloActivity a vyberte možnost **Přidat**a **Třída**. Pojmenujte novou třídu HelloActivity.cs.

5. Do souboru HelloActivity.cs přidejte následující `using` direktivy.

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    ```

6. Nastavit novou třídu jako dědění <xref:System.Activities.NativeActivity> přidáním základní třídy do deklarace třídy.

    ```csharp
    class HelloActivity : NativeActivity
    ```

7. Přidejte do třídy <xref:System.Activities.NativeActivity.Execute%2A> funkce přidáním metody.

    ```csharp
    protected override void Execute(NativeActivityContext context)
    {
        Console.WriteLine("Hello World!");
    }
    ```

8. Přepište <xref:System.Activities.NativeActivity.CacheMetadata%2A> metodu a zavolejte příslušnou metodu Add, aby modul runtime pracovního postupu mohl získat informace o proměnných, argumentech, podřízených a delegátech vlastní aktivity. Další informace najdete v tématu <xref:System.Activities.NativeActivityMetadata> třída.

9. K naplánování záložky použijte objekt.<xref:System.Activities.NativeActivityContext> Podrobnosti <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A> o tom, jak vytvořit, naplánovat a obnovit záložku, najdete v tématu.

    ```csharp
    protected override void Execute(NativeActivityContext context)
        {
            // Create a Bookmark and wait for it to be resumed.
            context.CreateBookmark(BookmarkName.Get(context),
                new BookmarkCallback(OnResumeBookmark));
        }
    ```
