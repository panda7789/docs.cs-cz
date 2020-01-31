---
title: Postup vytvoření uživatelsky definovaných výjimek s lokalizovanými zprávami výjimek
description: Naučte se vytvářet uživatelsky definované výjimky s lokalizovanými zprávami výjimek.
author: Youssef1313
dev_langs:
- csharp
- vb
ms.date: 09/13/2019
ms.openlocfilehash: 48e429a6379b0a13cb81f8db6fae27aa31409840
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794615"
---
# <a name="how-to-create-user-defined-exceptions-with-localized-exception-messages"></a>Postup vytvoření uživatelsky definovaných výjimek s lokalizovanými zprávami výjimek

V tomto článku se naučíte, jak vytvořit uživatelsky definované výjimky, které jsou zděděné ze základní <xref:System.Exception> třídy s lokalizovanými zprávami výjimek pomocí satelitních sestavení.

## <a name="create-custom-exceptions"></a>Vytváření vlastních výjimek

Rozhraní .NET obsahuje mnoho různých výjimek, které můžete použít. Nicméně v některých případech, pokud žádná z nich nevyhovuje vašim potřebám, můžete vytvořit vlastní výjimky.

Předpokládejme, že chcete vytvořit `StudentNotFoundException`, který obsahuje vlastnost `StudentName`.
Chcete-li vytvořit vlastní výjimku, použijte následující postup:

1. Vytvořte serializovatelný třídu, která dědí z <xref:System.Exception>. Název třídy by měl končit "výjimku":

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

1. Definujte jakékoli další vlastnosti a konstruktory:

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

## <a name="create-localized-exception-messages"></a>Vytvoření lokalizovaných zpráv výjimek

Vytvořili jste vlastní výjimku a můžete ji vyvolat kdekoli pomocí kódu podobného následujícímu:

```csharp
throw new StudentNotFoundException("The student cannot be found.", "John");
```

```vb
Throw New StudentNotFoundException("The student cannot be found.", "John")
```

Problém s předchozím řádkem je, že `"The student cannot be found."` je pouze konstantní řetězec. V lokalizované aplikaci chcete mít různé zprávy v závislosti na jazykové verzi uživatele.
Tato možnost je vhodná pro [satelitní sestavení](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) . Satelitní sestavení je knihovna DLL, která obsahuje prostředky pro určitý jazyk. Když požádáte o konkrétní prostředky v době běhu, modul CLR tento prostředek vyhledá v závislosti na jazykové verzi uživatele. Pokud se pro tuto jazykovou verzi nenajde žádné satelitní sestavení, použijí se prostředky výchozí jazykové verze.

Chcete-li vytvořit lokalizované zprávy o výjimce:

1. Vytvořte novou složku s názvem *Resources* , která bude obsahovat soubory prostředků.
1. Přidejte do něj nový soubor prostředků. Chcete-li to provést v aplikaci Visual Studio, klikněte pravým tlačítkem myši na složku v **Průzkumník řešení**a vyberte **Přidat** > **Nový** **soubor > prostředků**. Pojmenujte soubor *ExceptionMessages. resx*. Toto je výchozí soubor prostředků.
1. Přidejte dvojici název/hodnota pro vaši zprávu o výjimce, podobně jako na následujícím obrázku:

   ![Přidat prostředky do výchozí jazykové verze](media/add-resources-to-default-culture.jpg)

1. Přidejte nový soubor prostředků pro francouzštinu. Pojmenujte ho *ExceptionMessages.fr-fr. resx*.
1. Znovu přidejte dvojici název/hodnota pro zprávu o výjimce, ale s francouzskou hodnotou:

   ![Přidat prostředky do jazykové verze fr-FR](media/add-resources-to-fr-culture.jpg)

1. Po sestavení projektu by výstupní složka sestavení měla obsahovat složku *fr-FR* se souborem *. dll* , což je satelitní sestavení.
1. Výjimku vyvoláte jako následující kód:

    ```csharp
    var resourceManager = new ResourceManager("FULLY_QIALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly());
    throw new StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John");
    ```

    ```vb
    Dim resourceManager As New ResourceManager("FULLY_QIALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly())
    Throw New StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John")
    ```

    > [!NOTE]
    > Pokud je název projektu `TestProject` a soubor prostředků *ExceptionMessages. resx* se nachází ve složce *Resources* projektu, plně kvalifikovaný název souboru prostředků je `TestProject.Resources.ExceptionMessages`.

## <a name="see-also"></a>Viz také:

- [Vytvoření uživatelsky definovaných výjimek](how-to-create-user-defined-exceptions.md)
- [Vytváření satelitních sestavení pro aplikace klasické pracovní plochy](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [Base (C# Referenční dokumentace)](../../csharp/language-reference/keywords/base.md)
- [This (C# Referenční dokumentace)](../../csharp/language-reference/keywords/this.md)
