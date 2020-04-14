---
title: Jak vytvořit uživatelem definované výjimky s lokalizovanými zprávami o výjimkách
description: Zjistěte, jak vytvořit uživatelem definované výjimky s lokalizovanými zprávami o výjimkách
author: Youssef1313
dev_langs:
- csharp
- vb
ms.date: 09/13/2019
ms.openlocfilehash: fa0bbfdbfc9408302eec2edd4e4ee4503d2612c7
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243346"
---
# <a name="how-to-create-user-defined-exceptions-with-localized-exception-messages"></a>Jak vytvořit uživatelem definované výjimky s lokalizovanými zprávami o výjimkách

V tomto článku se dozvíte, jak vytvořit uživatelem definované výjimky, které jsou zděděny ze základní <xref:System.Exception> třídy s lokalizovanými zprávami o výjimkách pomocí satelitních sestavení.

## <a name="create-custom-exceptions"></a>Vytvořit vlastní výjimky

Rozhraní .NET obsahuje mnoho různých výjimek, které můžete použít. V některých případech, kdy žádný z nich nevyhovuje vašim potřebám, však můžete vytvořit vlastní výjimky.

Předpokládejme, že chcete vytvořit, `StudentNotFoundException` který `StudentName` obsahuje vlastnost.
Chcete-li vytvořit vlastní výjimku, postupujte takto:

1. Vytvořte serializovatelnou třídu, <xref:System.Exception>která dědí z . Název třídy by měl končit "Exception":

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception { }
    ```

    ```vb
    <Serializable>
    Public Class StudentNotFoundException
        Inherits Exception
    End Class
    ```

1. Přidejte výchozí konstruktory:

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception
    {
        public StudentNotFoundException() { }

        public StudentNotFoundException(string message)
            : base(message) { }

        public StudentNotFoundException(string message, Exception inner)
            : base(message, inner) { }
    }
    ```

    ```vb
    <Serializable>
    Public Class StudentNotFoundException
        Inherits Exception

        Public Sub New()
        End Sub

        Public Sub New(message As String)
            MyBase.New(message)
        End Sub

        Public Sub New(message As String, inner As Exception)
            MyBase.New(message, inner)
        End Sub
    End Class
    ```

1. Definujte všechny další vlastnosti a konstruktory:

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception
    {
        public string StudentName { get; }

        public StudentNotFoundException() { }

        public StudentNotFoundException(string message)
            : base(message) { }

        public StudentNotFoundException(string message, Exception inner)
            : base(message, inner) { }

        public StudentNotFoundException(string message, string studentName)
            : this(message)
        {
            StudentName = studentName;
        }
    }
    ```

    ```vb
    <Serializable>
    Public Class StudentNotFoundException
        Inherits Exception

        Public ReadOnly Property StudentName As String

        Public Sub New()
        End Sub

        Public Sub New(message As String)
            MyBase.New(message)
        End Sub

        Public Sub New(message As String, inner As Exception)
            MyBase.New(message, inner)
        End Sub

        Public Sub New(message As String, studentName As String)
            Me.New(message)
            StudentName = studentName
        End Sub
    End Class
    ```

## <a name="create-localized-exception-messages"></a>Vytvořit lokalizované zprávy o výjimce

Vytvořili jste vlastní výjimku a můžete ji vyvolat kdekoli s kódem, jako je následující:

```csharp
throw new StudentNotFoundException("The student cannot be found.", "John");
```

```vb
Throw New StudentNotFoundException("The student cannot be found.", "John")
```

Problém s předchozím řádkem je, že `"The student cannot be found."` je jen konstantní řetězec. V lokalizované aplikaci chcete mít různé zprávy v závislosti na jazykové verzi uživatele.
[Satelitní shromáždění](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) jsou dobrý způsob, jak to udělat. Satelitní sestavení je .dll, který obsahuje prostředky pro konkrétní jazyk. Když požádáte o konkrétní prostředky za běhu, CLR najde tento prostředek v závislosti na jazykové verzi uživatele. Pokud pro tuto jazykovou verzi není nalezeno žádné satelitní sestavení, použijí se prostředky výchozí jazykové verze.

Chcete-li vytvořit lokalizované zprávy o výjimce:

1. Vytvořte novou složku s názvem *Zdroje* pro uložení souborů prostředků.
1. Přidejte do něj nový soubor prostředků. Chcete-li to provést v sadě Visual Studio, klepněte pravým tlačítkem myši na složku v **Průzkumníkovi řešení**a vyberte **příkaz Přidat** > soubor prostředků**nové položky** > **Resources File**. Pojmenujte soubor *ExceptionMessages.resx*. Toto je výchozí soubor prostředků.
1. Přidejte dvojici název/hodnota pro zprávu o výjimce, například na následujícím obrázku:

   ![Přidání prostředků do výchozí jazykové verze](media/add-resources-to-default-culture.jpg)

1. Přidejte nový soubor prostředků pro francouzštinu. *Pojmenujte jej ExceptionMessages.fr-FR.resx*.
1. Přidejte dvojici název/hodnota pro zprávu o výjimce znovu, ale s francouzskou hodnotou:

   ![Přidání prostředků do jazykové verze fr-FR](media/add-resources-to-fr-culture.jpg)

1. Po sestavení projektu by výstupní složka sestavení měla obsahovat složku *fr-FR* se souborem *DLL,* což je satelitní sestavení.
1. Vyvolání výjimky s kódem, jako je následující:

    ```csharp
    var resourceManager = new ResourceManager("FULLY_QUALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly());
    throw new StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John");
    ```

    ```vb
    Dim resourceManager As New ResourceManager("FULLY_QUALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly())
    Throw New StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John")
    ```

    > [!NOTE]
    > Pokud je `TestProject` název projektu a soubor prostředků *ExceptionMessages.resx* je umístěn ve složce *Zdroje* projektu, `TestProject.Resources.ExceptionMessages`je plně kvalifikovaný název souboru prostředků .

## <a name="see-also"></a>Viz také

- [Jak vytvořit uživatelem definované výjimky](how-to-create-user-defined-exceptions.md)
- [Vytváření satelitních sestavení pro aplikace klasické pracovní plochy](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [base (Referenční dokumentace jazyka C#)](../../csharp/language-reference/keywords/base.md)
- [this (Referenční dokumentace jazyka C#)](../../csharp/language-reference/keywords/this.md)
