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
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a>Postupy: vytvoření projektu LINQ to DataSet v aplikaci Visual Studio

Různé typy projektů LINQ vyžadují určité odkazy na sestavení a importované obory názvů (Visual Basic) [](../../../csharp/language-reference/keywords/using-directive.md) nebo direktivyC#using (). Minimální požadavek pro LINQ je odkaz na *System. Core. dll* a direktivu `using` pro <xref:System.Linq>.

Tyto požadavky jsou zadány ve výchozím nastavení, pokud vytvoříte C# nový projekt konzolové aplikace v aplikaci Visual Studio 2017 nebo novější verzi. Pokud upgradujete projekt ze starší verze sady Visual Studio, bude pravděpodobně nutné dodat tyto odkazy související s LINQ ručně.

LINQ to DataSet vyžaduje dva další odkazy na *System. data. dll* a *System. data. DataSetExtensions. dll*.

> [!NOTE]
> Pokud vytváříte z příkazového řádku, musíte ručně odkazovat na knihovny DLL související s LINQ v *%programfiles%\Reference Assemblies\Microsoft\Framework\v3.5*.

## <a name="to-enable-linq-to-dataset-functionality"></a>Postup povolení funkcí LINQ to DataSet

Použijte následující postup, chcete-li povolit funkci LINQ to DataSet v existujícím projektu.

1. Přidejte odkazy na **System. Core**, **System. data**a **System. data. DataSetExtensions**.

   V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **odkazy** a vyberte možnost **Přidat odkaz**. V dialogovém okně **Správce odkazů** vyberte **System. Core**, **System. data**a **System. data. DataSetExtensions**. Vyberte **OK**.

1. Přidejte direktivy [using](../../../csharp/language-reference/keywords/using-directive.md) (nebo [příkazy imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) v Visual Basic) pro **System. data** a **System. Linq**.

   ```csharp
   using System.Data;
   using System.Linq;
   ```

1. Volitelně můžete přidat direktivu `using` (nebo `Imports` příkaz) pro **System. data. Common** nebo **System. data. SqlClient**v závislosti na tom, jak se připojujete k databázi.

## <a name="see-also"></a>Viz také:

- [Začínáme s LINQ to DataSet](getting-started-linq-to-dataset.md)
