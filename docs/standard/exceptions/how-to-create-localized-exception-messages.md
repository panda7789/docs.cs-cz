---
title: 'Postupy: vytváření uživatelsky definovaných výjimek s lokalizovanými zprávami výjimek'
description: Naučte se vytvářet uživatelsky definované výjimky s lokalizovanými zprávami výjimek.
author: Youssef1313
ms.author: ronpet
ms.date: 09/13/2019
ms.openlocfilehash: b4aa567fccda9354bc5959d6b9838d678d53abef
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696707"
---
# <a name="how-to-create-user-defined-exceptions-with-localized-exception-messages"></a>Postupy: vytváření uživatelsky definovaných výjimek s lokalizovanými zprávami výjimek

V tomto článku se naučíte, jak vytvořit uživatelsky definované výjimky, které jsou zděděné ze základní třídy <xref:System.Exception> s lokalizovanými zprávami výjimek pomocí satelitních sestavení.

## <a name="create-custom-exceptions"></a>Vytváření vlastních výjimek

Rozhraní .NET obsahuje mnoho různých výjimek, které můžete použít. Nicméně v některých případech, pokud žádná z nich nevyhovuje vašim potřebám, můžete vytvořit vlastní výjimky.

Předpokládejme, že chcete vytvořit `StudentNotFoundException`, který obsahuje vlastnost `StudentName`.
Chcete-li vytvořit vlastní výjimku, použijte následující postup:

1. Vytvořte serializovatelný třídu, která dědí z <xref:System.Exception>. Název třídy by měl končit "výjimku":

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception { }
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

## <a name="create-localized-exception-messages"></a>Vytvoření lokalizovaných zpráv výjimek

Vytvořili jste vlastní výjimku a můžete ji vyvolat kdekoli pomocí kódu podobného následujícímu:

```csharp
throw new StudentNotFoundException("The student cannot be found.", "John");
```

Problém s předchozím řádkem je, že `"The student cannot be found."` je pouze konstantní řetězec. V lokalizované aplikaci chcete mít různé zprávy v závislosti na jazykové verzi uživatele.
Tato možnost je vhodná pro [satelitní sestavení](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) . Satelitní sestavení je knihovna DLL, která obsahuje prostředky pro určitý jazyk. Když požádáte o konkrétní prostředky v době běhu, modul CLR tento prostředek vyhledá v závislosti na jazykové verzi uživatele. Pokud se pro tuto jazykovou verzi nenajde žádné satelitní sestavení, použijí se prostředky výchozí jazykové verze.

Chcete-li vytvořit lokalizované zprávy o výjimce:

1. Vytvořte novou složku s názvem *Resources* , která bude obsahovat soubory prostředků.
1. Přidejte do něj nový soubor prostředků. Provedete to tak, že v aplikaci Visual Studio kliknete pravým tlačítkem na složku v **Průzkumník řešení**a vyberete **přidat** **soubor prostředků** > **nové položky** > . Pojmenujte soubor *ExceptionMessages. resx*. Toto je výchozí soubor prostředků.
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

  > [!NOTE]
  > Pokud je název projektu `TestProject` a soubor prostředků *ExceptionMessages. resx* se nachází ve složce *Resources* projektu, plně kvalifikovaný název souboru prostředků je `TestProject.Resources.ExceptionMessages`.

## <a name="see-also"></a>Viz také:

- [Vytvoření uživatelsky definovaných výjimek](how-to-create-user-defined-exceptions.md)
- [Vytváření satelitních sestavení pro aplikace klasické pracovní plochy](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [Base (C# Referenční dokumentace)](../../csharp/language-reference/keywords/base.md)
- [This (C# Referenční dokumentace)](../../csharp/language-reference/keywords/this.md)
