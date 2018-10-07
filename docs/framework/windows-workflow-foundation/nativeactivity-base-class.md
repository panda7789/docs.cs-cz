---
title: Základní třída NativeActivity
ms.date: 03/30/2017
ms.assetid: 254a4c50-425b-426d-a32f-0f7234925bac
ms.openlocfilehash: 40eff2e597763fd492b3051df1a91622e7a60672
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48842032"
---
# <a name="nativeactivity-base-class"></a>Základní třída NativeActivity

<xref:System.Activities.NativeActivity> je abstraktní třída s konstruktorem chráněné. Stejně jako <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> se používá k zápisu imperativní chování implementací <xref:System.Activities.NativeActivity.Execute%2A> metody. Na rozdíl od <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> má přístup ke všem vystavené funkcím modulu runtime pracovního postupu pomocí <xref:System.Activities.NativeActivityContext> předán objekt <xref:System.Activities.NativeActivity.Execute%2A> metody.

## <a name="using-nativeactivitycontext"></a>Pomocí NativeActivityContext
 Funkce modulu runtime pracovního postupu je přístupný z v rámci <xref:System.Activities.NativeActivity.Execute%2A> metoda pomocí členy `context` parametr typu <xref:System.Activities.NativeActivityContext>. Funkcí dostupných prostřednictvím <xref:System.Activities.NativeActivityContext> patří následující:

-   Získání a nastavení proměnných a argumentů příkazu.

-   Plánování podřízené aktivity s <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>

-   Přerušení aktivity spuštění pomocí <xref:System.Activities.NativeActivityContext.Abort%2A>.

-   Zrušení podřízené spuštění pomocí <xref:System.Activities.NativeActivityContext.CancelChild%2A> a <xref:System.Activities.NativeActivityContext.CancelChildren%2A>.

-   Přístup k záložky aktivity pomocí metod, jako <xref:System.Activities.NativeActivityContext.CreateBookmark%2A>, <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A>, a <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A>.

-   Vlastní sledování funkce pomocí <xref:System.Activities.CodeActivityContext.Track%2A>.

-   Přístup k provádění vlastnosti a hodnotu vlastnosti pomocí aktivity <xref:System.Activities.CodeActivityContext.GetProperty%2A> a <xref:System.Activities.NativeActivityContext.GetValue%2A>.

-   Plánování aktivit akcí a funkcí pomocí <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> a <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A>.

### <a name="to-create-a-custom-activity-that-inherits-from-nativeactivity"></a>Chcete-li vytvořit vlastní aktivitu, která dědí z nativeactivity načte jako

1.  Otevřete Visual Studio 2010.

2.  Vyberte **souboru**, **nové**a potom **projektu**. Vyberte **Workflow 4.0** pod **Visual C#** v **typy projektů** okna a vyberte **v2010** uzlu. Vyberte **knihovny aktivit** v **šablony** okna. Název nového projektu HelloActivity.

3.  Klikněte pravým tlačítkem na Activity1.xaml HelloActivity projektu a vyberte **odstranit**.

4.  Klikněte pravým tlačítkem na projekt HelloActivity a vyberte **přidat**a potom **třídy**. Pojmenujte novou třídu HelloActivity.cs.

5.  V souboru HelloActivity.cs, přidejte následující `using` direktivy.

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    ```

6.  Ujistěte se, nová třída dědila z <xref:System.Activities.NativeActivity> přidáním základní třídu pro deklaraci třídy.

    ```csharp
    class HelloActivity : NativeActivity
    ```

7.  Přidání funkce do třídy tak, že přidáte <xref:System.Activities.NativeActivity.Execute%2A> metody.

    ```csharp
    protected override void Execute(NativeActivityContext context)
    {
        Console.WriteLine("Hello World!");
    }
    ```

8.  Přepsat <xref:System.Activities.NativeActivity.CacheMetadata%2A> metoda a volání odpovídající metody Add umožní modulu runtime pracovního postupu vědět o proměnné, argumenty, podřízené položky a delegáti vlastní aktivity. Další informace najdete v článku <xref:System.Activities.NativeActivityMetadata> třídy.

9. Použití <xref:System.Activities.NativeActivityContext> objekt naplánování záložku. Zobrazit <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A> podrobnosti o tom, jak vytvořit, naplánovat a obnovení záložku.

    ```
    protected override void Execute(NativeActivityContext context)
        {
            // Create a Bookmark and wait for it to be resumed.
            context.CreateBookmark(BookmarkName.Get(context),
                new BookmarkCallback(OnResumeBookmark));
        }
    ```