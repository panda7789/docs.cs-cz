---
title: Vytvoření LINQ to DataSet projektu v sadě Visual Studio
ms.date: 08/15/2018
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
ms.openlocfilehash: 22763d3b9581d09d7bdda0c09480f8d36bb8e2ec
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185557"
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a><span data-ttu-id="74cad-102">Postupy: vytvoření LINQ to DataSet projektu v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="74cad-102">How to: Create a LINQ to DataSet project In Visual Studio</span></span>

<span data-ttu-id="74cad-103">Různé typy projektů LINQ vyžadovat některé odkazy na sestavení a importovaných oborů názvů (Visual Basic) nebo [pomocí](../../../csharp/language-reference/keywords/using-directive.md) direktivy (C#).</span><span class="sxs-lookup"><span data-stu-id="74cad-103">The different types of LINQ projects require certain assembly references and imported namespaces (Visual Basic) or [using](../../../csharp/language-reference/keywords/using-directive.md) directives (C#).</span></span> <span data-ttu-id="74cad-104">Minimální požadavky pro funkci LINQ je odkaz na *System.Core.dll* a `using` směrnice pro <xref:System.Linq>.</span><span class="sxs-lookup"><span data-stu-id="74cad-104">The minimum requirement for LINQ is a reference to *System.Core.dll* and a `using` directive for <xref:System.Linq>.</span></span>

<span data-ttu-id="74cad-105">Pokud vytvoříte nový projekt C# konzoly aplikace v sadě Visual Studio 2017, jsou ve výchozím nastavení zadávají tyto požadavky.</span><span class="sxs-lookup"><span data-stu-id="74cad-105">These requirements are supplied by default if you create a new C# console app project in Visual Studio 2017.</span></span> <span data-ttu-id="74cad-106">Pokud upgradujete projekt ze starší verze sady Visual Studio, bude pravděpodobně k poskytování těchto odkazů souvisejících s LINQ ručně.</span><span class="sxs-lookup"><span data-stu-id="74cad-106">If you're upgrading a project from an earlier version of Visual Studio, you might have to supply these LINQ-related references manually.</span></span>

<span data-ttu-id="74cad-107">Technologie LINQ to DataSet vyžaduje dva další odkazy *System.Data.dll* a *System.Data.DataSetExtensions.dll*.</span><span class="sxs-lookup"><span data-stu-id="74cad-107">LINQ to DataSet requires two additional references to *System.Data.dll* and *System.Data.DataSetExtensions.dll*.</span></span>

> [!NOTE]
> <span data-ttu-id="74cad-108">Pokud sestavujete z příkazového řádku, je třeba ručně odkazovat související s LINQ knihovny DLL v *%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.5*.</span><span class="sxs-lookup"><span data-stu-id="74cad-108">If you're building from a command prompt, you must manually reference the LINQ-related DLLs in *%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.5*.</span></span>

## <a name="to-enable-linq-to-dataset-functionality"></a><span data-ttu-id="74cad-109">Kvůli povolení jazyka LINQ k datové sadě funkcí</span><span class="sxs-lookup"><span data-stu-id="74cad-109">To enable LINQ to DataSet functionality</span></span>

<span data-ttu-id="74cad-110">Postupujte podle těchto kroků kvůli povolení jazyka LINQ k datové sadě funkcí v existujícím projektu.</span><span class="sxs-lookup"><span data-stu-id="74cad-110">Follow these steps to enable LINQ to DataSet functionality in an existing project.</span></span>

1. <span data-ttu-id="74cad-111">Přidání odkazů na **System.Core**, **System.Data**, a **System.Data.DataSetExtensions**.</span><span class="sxs-lookup"><span data-stu-id="74cad-111">Add references to **System.Core**, **System.Data**, and **System.Data.DataSetExtensions**.</span></span>

   <span data-ttu-id="74cad-112">V **Průzkumníka řešení**, klikněte pravým tlačítkem na **odkazy** uzel a vyberte možnost **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="74cad-112">In **Solution Explorer**, right-click on the **References** node and select **Add Reference**.</span></span> <span data-ttu-id="74cad-113">V **správce odkazů** dialogu **System.Core**, **System.Data**, a **System.Data.DataSetExtensions**.</span><span class="sxs-lookup"><span data-stu-id="74cad-113">In the **Reference Manager** dialog box, select **System.Core**, **System.Data**, and **System.Data.DataSetExtensions**.</span></span> <span data-ttu-id="74cad-114">Vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="74cad-114">Select **OK**.</span></span>

1. <span data-ttu-id="74cad-115">Přidat [pomocí](../../../csharp/language-reference/keywords/using-directive.md) direktivy (nebo [importuje příkazy](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) v jazyce Visual Basic) pro **System.Data** a **System.Linq**.</span><span class="sxs-lookup"><span data-stu-id="74cad-115">Add [using](../../../csharp/language-reference/keywords/using-directive.md) directives (or [Imports statements](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) in Visual Basic) for **System.Data** and **System.Linq**.</span></span>

   ```csharp
   using System.Data;
   using System.Linq;
   ```

1. <span data-ttu-id="74cad-116">Volitelně můžete přidat `using` – direktiva (nebo `Imports` příkaz) pro **System.Data.Common** nebo **System.Data.SqlClient**, v závislosti na tom, jak připojit k databázi.</span><span class="sxs-lookup"><span data-stu-id="74cad-116">Optionally, add a `using` directive (or `Imports` statement) for **System.Data.Common** or **System.Data.SqlClient**, depending on how you connect to the database.</span></span>

## <a name="see-also"></a><span data-ttu-id="74cad-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="74cad-117">See also</span></span>

- [<span data-ttu-id="74cad-118">Začínáme s jazykem LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="74cad-118">Get started with LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)
