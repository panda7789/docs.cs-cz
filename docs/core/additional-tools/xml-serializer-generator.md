---
title: Generátor serializátorů Microsoft XML
description: Přehled generátoru serializátorů Microsoft XML Pomocí generátoru serializátoru XML vygenerujte sestavení serializace XML pro typy obsažené ve vašem projektu.
author: mlacouture
ms.date: 01/19/2017
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c3f1fcda8a8a6abc58d35bf37e51485bb3590fa3
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794634"
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a>Používání generátoru Microsoft XML serializátoru v .NET Core

V tomto kurzu se naučíte používat generátor serializátoru Microsoft XML v aplikaci C# .NET Core. V průběhu tohoto kurzu se naučíte:

> [!div class="checklist"]
>
> - Vytvoření aplikace v .NET Core
> - Přidání odkazu do balíčku Microsoft.XmlSerializer.Generator
> - Úprava souboru MyApp.csproj a přidání závislostí
> - Přidání třídy a objektu XmlSerializer
> - Sestavení a spuštění aplikace

Podobně jako [generátor serializátorů XML (Sgen. exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) pro .NET Framework je [balíček NuGet Microsoft. XmlSerializer. Generator](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) ekvivalentem pro projekty .NET Core a .NET Standard. Vytvoří sestavení serializace XML pro typy obsažené v sestavení pro zlepšení výkonu při spuštění serializace XML při serializaci nebo deserializaci objektů těchto typů pomocí <xref:System.Xml.Serialization.XmlSerializer>.

## <a name="prerequisites"></a>Požadavky

Pro absolvování tohoto kurzu potřebujete:

- [.NET Core 2,1 SDK](https://dotnet.microsoft.com/download) nebo novější.
- Váš oblíbený editor kódu.

> [!TIP]
> Potřebujete nainstalovat editor kódu? Vyzkoušejte [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!

## <a name="use-microsoft-xml-serializer-generator-in-a-net-core-console-application"></a>Použití generátoru Microsoft XML serializátoru v konzolové aplikaci .NET Core

Následující pokyny ukazují, jak používat generátor serializátoru XML v konzolové aplikaci .NET Core.

### <a name="create-a-net-core-console-application"></a>Vytvoření konzolové aplikace .NET Core

Otevřete příkazový řádek a vytvořte složku s názvem *MyApp*. Přejděte do složky, kterou jste vytvořili, a zadejte následující příkaz:

```dotnetcli
dotnet new console
```

### <a name="add-a-reference-to-the-microsoftxmlserializergenerator-package-in-the-myapp-project"></a>Přidání odkazu na balíček Microsoft. XmlSerializer. Generator v projektu MyApp

Pomocí [`dotnet add package`](../tools/dotnet-add-package.md) příkazu přidejte odkaz do projektu.

Zadejte:

```dotnetcli
dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
```

### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a>Po přidání balíčku ověřit změny v MyApp. csproj

Otevřete Editor kódu a pojďme začít! Pořád pracujeme z adresáře *MyApp* , ve kterém jsme aplikaci sestavili.

Otevřete *MyApp. csproj* v textovém editoru.

Po spuštění [`dotnet add package`](../tools/dotnet-add-package.md) příkazu jsou do souboru *MyApp. csproj* přidány následující řádky:

 ```xml
 <ItemGroup>
    <PackageReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-another-itemgroup-section-for-net-core-cli-tool-support"></a>Přidání další části skupin položek pro podporu .NET Core CLI nástrojů

Za `ItemGroup` část, kterou jsme zkontrolovali, přidejte následující řádky:

 ```xml
 <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-a-class-in-the-application"></a>Přidání třídy do aplikace

Otevřete *program.cs* v textovém editoru. Přidejte třídu s názvem *MyClass* v *program.cs*.

```csharp
public class MyClass
{
   public int Value;
}
```

### <a name="create-an-xmlserializer-for-myclass"></a>Vytvoření `XmlSerializer` pro MyClass

Přidejte následující řádek do *Main* a vytvořte tak `XmlSerializer` pro MyClass:

```csharp
var serializer = new System.Xml.Serialization.XmlSerializer(typeof(MyClass));
```

### <a name="build-and-run-the-application"></a>Sestavení a spuštění aplikace

Pořád ve složce *MyApp* spusťte aplikaci prostřednictvím [`dotnet run`](../tools/dotnet-run.md) a automaticky načte a použije předem vygenerované serializace za běhu.

V okně konzoly zadejte následující příkaz:

```dotnetcli
dotnet run
```

> [!NOTE]
> [`dotnet run`](../tools/dotnet-run.md)volá [`dotnet build`](../tools/dotnet-build.md) , aby se zajistilo sestavení cílů sestavení, a pak volání `dotnet <assembly.dll>` pro spuštění cílové aplikace.

> [!IMPORTANT]
> Příkazy a kroky uvedené v tomto kurzu pro spuštění aplikace jsou používány pouze během doby vývoje. Až budete připraveni k nasazení aplikace, podívejte se na různé [strategie nasazení](../deploying/index.md) pro aplikace .NET Core a [`dotnet publish`](../tools/dotnet-publish.md) příkaz.

Pokud je vše úspěšné, sestavení s názvem *MyApp. XmlSerializers. dll* je vygenerováno ve výstupní složce.

Blahopřejeme! Právě jste:
> [!div class="checklist"]
>
> - Vytvořili jste aplikaci .NET Core.
> - Byl přidán odkaz na balíček Microsoft. XmlSerializer. Generator.
> - Úpravou MyApp. csproj přidejte závislosti.
> - Přidala se třída a XmlSerializer.
> - Sestavila a spustila aplikaci.

## <a name="related-resources"></a>Související prostředky

- [Představení serializace XML](../../standard/serialization/introducing-xml-serialization.md)
- [Postup při serializaci pomocí XmlSerializer (C#)](../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
- [Postupy: serializace pomocí XmlSerializer (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
