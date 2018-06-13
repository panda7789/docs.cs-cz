---
title: NativeActivity základní třída
ms.date: 03/30/2017
ms.assetid: 254a4c50-425b-426d-a32f-0f7234925bac
ms.openlocfilehash: ca4a497f1e78989f9488507015526214ead6cae7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517264"
---
# <a name="nativeactivity-base-class"></a>NativeActivity základní třída
<xref:System.Activities.NativeActivity> je abstraktní třídy chráněný konstruktor. Jako <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> slouží k zápisu imperativní chování implementací <xref:System.Activities.NativeActivity.Execute%2A> metoda. Na rozdíl od <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> má přístup ke všem zveřejněné funkce modulu runtime pracovního postupu pomocí <xref:System.Activities.NativeActivityContext> byl předán objekt <xref:System.Activities.NativeActivity.Execute%2A> metoda.  
  
## <a name="using-nativeactivitycontext"></a>Pomocí NativeActivityContext  
 Funkce modulu runtime pracovního postupu je přístupná prostřednictvím <xref:System.Activities.NativeActivity.Execute%2A> metoda pomocí členy `context` parametr typu <xref:System.Activities.NativeActivityContext>. Funkcí dostupných prostřednictvím <xref:System.Activities.NativeActivityContext> patří:  
  
-   Získání a nastavení proměnných a argumenty.  
  
-   Plánování podřízené aktivity s <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>  
  
-   Přerušení aktivity provádění pomocí <xref:System.Activities.NativeActivityContext.Abort%2A>.  
  
-   Ruší podřízené provádění pomocí <xref:System.Activities.NativeActivityContext.CancelChild%2A> a <xref:System.Activities.NativeActivityContext.CancelChildren%2A>.  
  
-   Přístup k aktivity záložky pomocí těchto metod jako <xref:System.Activities.NativeActivityContext.CreateBookmark%2A>, <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A>, a <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A>.  
  
-   Vlastní sledování funkce pomocí <xref:System.Activities.CodeActivityContext.Track%2A>.  
  
-   Přístup k provádění vlastnosti a hodnotu vlastnosti pomocí aktivity <xref:System.Activities.CodeActivityContext.GetProperty%2A> a <xref:System.Activities.NativeActivityContext.GetValue%2A>.  
  
-   Plánování aktivity akcí a funkcí pomocí <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> a <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A>.  
  
#### <a name="to-create-a-custom-activity-that-inherits-from-nativeactivity"></a>Chcete-li vytvořit vlastní aktivitu, která dědí z NativeActivity  
  
1.  Otevřete[!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
2.  Vyberte **soubor**, **nové**a potom **projektu**. Vyberte **Workflow 4.0** pod **Visual C#** v **typy projektů** a vyberte **v2010** uzlu. Vyberte **knihovna aktivit** v **šablony** okno. Název nového projektu HelloActivity.  
  
3.  Klikněte pravým tlačítkem na Activity1.xaml v HelloActivity projektu a vyberte **odstranit**.  
  
4.  Klikněte pravým tlačítkem na projekt HelloActivity a vyberte **přidat**a potom **třída**. Pojmenujte novou třídu HelloActivity.cs.  
  
5.  V souboru HelloActivity.cs, přidejte následující `using` direktivy.  
  
    ```csharp  
    using System.Activities;  
    using System.Activities.Statements;  
    ```  
  
6.  Ujistěte se, nové třídy dědí <xref:System.Activities.NativeActivity> přidáním základní třídu pro deklaraci třídy.  
  
    ```csharp  
    class HelloActivity : NativeActivity  
    ```  
  
7.  Přidání funkce do třídy přidáním <xref:System.Activities.NativeActivity.Execute%2A> metoda.  
  
    ```csharp  
    protected override void Execute(NativeActivityContext context)  
    {  
        Console.WriteLine("Hello World!");  
    }  
    ```  
  
8.  Přepsání <xref:System.Activities.NativeActivity.CacheMetadata%2A> metoda a volání odpovídající metodu přidat umožníte modulu runtime pracovního postupu vědět o proměnné vlastní aktivity, argumenty, děti a delegáti. Další informace najdete v článku <xref:System.Activities.NativeActivityMetadata> třídy.  
  
9. Použití <xref:System.Activities.NativeActivityContext> objekt, který chcete naplánovat záložky. V tématu <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A> podrobnosti o tom, jak vytvořit, naplánovat a obnovit záložky.  
  
    ```  
    protected override void Execute(NativeActivityContext context)  
        {  
            // Create a Bookmark and wait for it to be resumed.  
            context.CreateBookmark(BookmarkName.Get(context),   
                new BookmarkCallback(OnResumeBookmark));  
        }  
    ```
