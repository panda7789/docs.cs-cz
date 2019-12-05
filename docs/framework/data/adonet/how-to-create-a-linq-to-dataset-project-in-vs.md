---
title: Vytvoření projektu LINQ to DataSet v aplikaci Visual Studio
ms.date: 08/15/2018
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
ms.openlocfilehash: 91032766248b11e51b90aa788b1c64c140347c25
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802023"
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a><span data-ttu-id="cdfc6-102">Postupy: vytvoření projektu LINQ to DataSet v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cdfc6-102">How to: Create a LINQ to DataSet project in Visual Studio</span></span>

<span data-ttu-id="cdfc6-103">Různé typy projektů LINQ vyžadují určité odkazy na sestavení a importované obory názvů (Visual Basic) [](../../../csharp/language-reference/keywords/using-directive.md) nebo direktivyC#using ().</span><span class="sxs-lookup"><span data-stu-id="cdfc6-103">The different types of LINQ projects require certain assembly references and imported namespaces (Visual Basic) or [using](../../../csharp/language-reference/keywords/using-directive.md) directives (C#).</span></span> <span data-ttu-id="cdfc6-104">Minimální požadavek pro LINQ je odkaz na *System. Core. dll* a direktivu `using` pro <xref:System.Linq>.</span><span class="sxs-lookup"><span data-stu-id="cdfc6-104">The minimum requirement for LINQ is a reference to *System.Core.dll* and a `using` directive for <xref:System.Linq>.</span></span>

<span data-ttu-id="cdfc6-105">Tyto požadavky jsou zadány ve výchozím nastavení, pokud vytvoříte C# nový projekt konzolové aplikace v aplikaci Visual Studio 2017 nebo novější verzi.</span><span class="sxs-lookup"><span data-stu-id="cdfc6-105">These requirements are supplied by default if you create a new C# console app project in Visual Studio 2017 or a later version.</span></span> <span data-ttu-id="cdfc6-106">Pokud upgradujete projekt ze starší verze sady Visual Studio, bude pravděpodobně nutné dodat tyto odkazy související s LINQ ručně.</span><span class="sxs-lookup"><span data-stu-id="cdfc6-106">If you're upgrading a project from an earlier version of Visual Studio, you might have to supply these LINQ-related references manually.</span></span>

<span data-ttu-id="cdfc6-107">LINQ to DataSet vyžaduje dva další odkazy na *System. data. dll* a *System. data. DataSetExtensions. dll*.</span><span class="sxs-lookup"><span data-stu-id="cdfc6-107">LINQ to DataSet requires two additional references to *System.Data.dll* and *System.Data.DataSetExtensions.dll*.</span></span>

> [!NOTE]
> <span data-ttu-id="cdfc6-108">Pokud vytváříte z příkazového řádku, musíte ručně odkazovat na knihovny DLL související s LINQ v *%programfiles%\Reference Assemblies\Microsoft\Framework\v3.5*.</span><span class="sxs-lookup"><span data-stu-id="cdfc6-108">If you're building from a command prompt, you must manually reference the LINQ-related DLLs in *%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.5*.</span></span>

## <a name="to-enable-linq-to-dataset-functionality"></a><span data-ttu-id="cdfc6-109">Postup povolení funkcí LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="cdfc6-109">To enable LINQ to DataSet functionality</span></span>

<span data-ttu-id="cdfc6-110">Použijte následující postup, chcete-li povolit funkci LINQ to DataSet v existujícím projektu.</span><span class="sxs-lookup"><span data-stu-id="cdfc6-110">Follow these steps to enable LINQ to DataSet functionality in an existing project.</span></span>

1. <span data-ttu-id="cdfc6-111">Přidejte odkazy na **System. Core**, **System. data**a **System. data. DataSetExtensions**.</span><span class="sxs-lookup"><span data-stu-id="cdfc6-111">Add references to **System.Core**, **System.Data**, and **System.Data.DataSetExtensions**.</span></span>

   <span data-ttu-id="cdfc6-112">V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **odkazy** a vyberte možnost **Přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="cdfc6-112">In **Solution Explorer**, right-click on the **References** node and select **Add Reference**.</span></span> <span data-ttu-id="cdfc6-113">V dialogovém okně **Správce odkazů** vyberte **System. Core**, **System. data**a **System. data. DataSetExtensions**.</span><span class="sxs-lookup"><span data-stu-id="cdfc6-113">In the **Reference Manager** dialog box, select **System.Core**, **System.Data**, and **System.Data.DataSetExtensions**.</span></span> <span data-ttu-id="cdfc6-114">Vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="cdfc6-114">Select **OK**.</span></span>

1. <span data-ttu-id="cdfc6-115">Přidejte direktivy [using](../../../csharp/language-reference/keywords/using-directive.md) (nebo [příkazy imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) v Visual Basic) pro **System. data** a **System. Linq**.</span><span class="sxs-lookup"><span data-stu-id="cdfc6-115">Add [using](../../../csharp/language-reference/keywords/using-directive.md) directives (or [Imports statements](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) in Visual Basic) for **System.Data** and **System.Linq**.</span></span>

   ```csharp
   using System.Data;
   using System.Linq;
   ```

1. <span data-ttu-id="cdfc6-116">Volitelně můžete přidat direktivu `using` (nebo `Imports` příkaz) pro **System. data. Common** nebo **System. data. SqlClient**v závislosti na tom, jak se připojujete k databázi.</span><span class="sxs-lookup"><span data-stu-id="cdfc6-116">Optionally, add a `using` directive (or `Imports` statement) for **System.Data.Common** or **System.Data.SqlClient**, depending on how you connect to the database.</span></span>

## <a name="see-also"></a><span data-ttu-id="cdfc6-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cdfc6-117">See also</span></span>

- [<span data-ttu-id="cdfc6-118">Začínáme s LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="cdfc6-118">Get started with LINQ to DataSet</span></span>](getting-started-linq-to-dataset.md)
