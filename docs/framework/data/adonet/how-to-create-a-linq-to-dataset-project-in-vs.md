---
title: "Postupy: vytvoření LINQ na DataSet projekt v sadě Visual Studio"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 6710d3e9bf52ff10ee8dd545161f0858001f2c40
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a>Postupy: vytvoření LINQ na DataSet projekt v sadě Visual Studio
Různé typy [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] projekty vyžadovat určité importovaných oborů názvů (Visual Basic) nebo `using` direktivy (C#) a odkazy. Minimální požadavek je odkaz na System.Core.dll a `using` direktivy pro <xref:System.Linq>. Ve výchozím nastavení, tyto se zadávají v případě, že vytvoříte novou [!INCLUDE[csharp_orcas_long](../../../../includes/csharp-orcas-long-md.md)] projektu. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]také vyžaduje odkaz na System.Data.dll a System.Data.DataSetExtensions.dll a `Imports` (Visual Basic) nebo `using` – direktiva (C#).  
  
 Pokud provádíte upgrade projektu ze starší verze sady Visual Studio, můžete chtít zadat tyto odkazy na související LINQ ručně. Budete také muset ručně nastavte projekt, který má cílové rozhraní .NET Framework verze 3.5.  
  
> [!NOTE]
>  Pokud vytváříte z příkazového řádku, je nutné ručně odkazovat související LINQ knihovny DLL v `drive` **:**\Program Files\Reference Assemblies\Microsoft\Framework\v3.5.  
  
### <a name="to-target-the-net-framework-35"></a>Cíl pro rozhraní .NET Framework 3.5  
  
1.  V [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)], vytvořte nový projekt Visual Basic a C#. Alternativně můžete otevřít projekt Visual Basic a C#, která byla vytvořena v sadě Visual Studio 2005 a postupujte podle pokynů a převeďte ho na [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] projektu.  
  
2.  Pro projekt C#, klikněte na tlačítko **projektu** nabídce a pak klikněte na tlačítko **vlastnosti**.  
  
    1.  V **aplikace** stránka vlastností, vyberte rozhraní .NET Framework 3.5 v **cílové rozhraní** rozevíracího seznamu.  
  
3.  Projektu jazyka Visual Basic, klikněte na tlačítko **projektu** nabídce a pak klikněte na tlačítko **vlastnosti**.  
  
    1.  V **zkompilovat** stránce vlastností, klikněte na tlačítko **Upřesnit možnosti kompilace** a pak vyberte rozhraní .NET Framework 3.5 v **cílové rozhraní (všechny konfigurace)** rozevíracího seznamu.  
  
4.  Na **projektu** nabídky, klikněte na tlačítko **přidat odkaz na**, klikněte na tlačítko **rozhraní .NET** kartě, přejděte dolů k položce **System.Core**, klikněte na něj a potom klikněte na tlačítko  **OK**.  
  
5.  Přidat `using` direktivy nebo importované obor názvů pro <xref:System.Linq> k souboru zdrojového kódu nebo projektu.  
  
     Další informace najdete v tématu [using – direktiva](~/docs/csharp/language-reference/keywords/using-directive.md) nebo [postupy: Přidání nebo odebrání importovaných oborů názvů (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).  
  
### <a name="to-enable-linq-to-dataset-functionality"></a>Chcete-li povolit LINQ na datovou sadu funkcí  
  
1.  V případě potřeby, postupujte podle kroků výše v tomto tématu se přidat odkaz na System.Core.dll a `using` direktivy nebo importované obor názvů pro System.Linq.  
  
2.  V C# nebo Visual Basic, klikněte **projektu** nabídky a pak klikněte na **přidat odkaz na**.  
  
3.  V **přidat odkaz na** dialogové okno, klikněte na tlačítko **.NET** kartě, pokud není v horní části. Přejděte dolů k položce **System.Data** a **System.Data.DataSetExtensions** a klikněte na ně. Klikněte **OK** tlačítko.  
  
4.  Přidat `using` direktivy nebo importované obor názvů pro <xref:System.Data> k souboru zdrojového kódu nebo projektu. Další informace najdete v tématu [using – direktiva](~/docs/csharp/language-reference/keywords/using-directive.md) nebo [postupy: Přidání nebo odebrání importovaných oborů názvů (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).  
  
5.  Přidáte odkaz na System.Data.DataSetExtensions.dll pro LINQ na datovou sadu funkcí. Přidáte odkaz na System.Data.dll, pokud ještě neexistuje.  
  
6.  Volitelně lze přidat `using` direktivy nebo importované obor názvů pro `System.Data.Common` nebo `System.Data.SqlClient`, v závislosti na tom, jak připojit k databázi.  
  
## <a name="see-also"></a>Viz také  
 [Začínáme](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
 [Začínáme s jazykem LINQ](http://msdn.microsoft.com/en-us/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9)
