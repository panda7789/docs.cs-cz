---
title: Vytvoření LINQ to DataSet projektu v sadě Visual Studio
ms.date: 08/15/2018
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
ms.openlocfilehash: 22763d3b9581d09d7bdda0c09480f8d36bb8e2ec
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52297013"
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a>Postupy: vytvoření LINQ to DataSet projektu v sadě Visual Studio

Různé typy projektů LINQ vyžadovat některé odkazy na sestavení a importovaných oborů názvů (Visual Basic) nebo [pomocí](../../../csharp/language-reference/keywords/using-directive.md) direktivy (C#). Minimální požadavky pro funkci LINQ je odkaz na *System.Core.dll* a `using` směrnice pro <xref:System.Linq>.

Pokud vytvoříte nový projekt C# konzoly aplikace v sadě Visual Studio 2017, jsou ve výchozím nastavení zadávají tyto požadavky. Pokud upgradujete projekt ze starší verze sady Visual Studio, bude pravděpodobně k poskytování těchto odkazů souvisejících s LINQ ručně.

Technologie LINQ to DataSet vyžaduje dva další odkazy *System.Data.dll* a *System.Data.DataSetExtensions.dll*.

> [!NOTE]
> Pokud sestavujete z příkazového řádku, je třeba ručně odkazovat související s LINQ knihovny DLL v *%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.5*.

## <a name="to-enable-linq-to-dataset-functionality"></a>Kvůli povolení jazyka LINQ k datové sadě funkcí

Postupujte podle těchto kroků kvůli povolení jazyka LINQ k datové sadě funkcí v existujícím projektu.

1. Přidání odkazů na **System.Core**, **System.Data**, a **System.Data.DataSetExtensions**.

   V **Průzkumníka řešení**, klikněte pravým tlačítkem na **odkazy** uzel a vyberte možnost **přidat odkaz**. V **správce odkazů** dialogu **System.Core**, **System.Data**, a **System.Data.DataSetExtensions**. Vyberte **OK**.

1. Přidat [pomocí](../../../csharp/language-reference/keywords/using-directive.md) direktivy (nebo [importuje příkazy](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) v jazyce Visual Basic) pro **System.Data** a **System.Linq**.

   ```csharp
   using System.Data;
   using System.Linq;
   ```

1. Volitelně můžete přidat `using` – direktiva (nebo `Imports` příkaz) pro **System.Data.Common** nebo **System.Data.SqlClient**, v závislosti na tom, jak připojit k databázi.

## <a name="see-also"></a>Viz také:

- [Začínáme s jazykem LINQ to DataSet](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)
