---
title: Generátor serializátor XML společnosti Microsoft
description: Přehled generátor serializátor XML společnosti Microsoft. Generátor serializátor XML můžete generovat sestavení serializace XML pro typy obsažené v projektu.
author: mlacouture
ms.date: 01/19/2017
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 9070c42a7cef389a2a13f6be6f26f7dafd7f25e2
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244775"
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a>Pomocí generátor serializátor XML společnosti Microsoft v rozhraní .NET Core

V tomto kurzu se naučíte, jak používat generátor serializátor XML společnosti Microsoft v C# aplikaci .NET Core. V průběhu tohoto kurzu se dozvíte:

> [!div class="checklist"]
> * Jak vytvořit aplikaci .NET Core
> * Jak přidat odkaz na balíček Microsoft.XmlSerializer.Generator
> * Úprava vaše MyApp.csproj přidat závislosti
> * Přidání třídy a objektu XmlSerializer
> * Jak sestavit a spustit aplikaci

Podobně jako [generátor serializátor Xml (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) pro rozhraní .NET Framework [balíček Microsoft.XmlSerializer.Generator NuGet](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) ekvivalent pro projekty .NET Core a .NET Standard. Vytvoří sestavení serializace XML pro typy, které jsou obsaženy v sestavení, které chcete zlepšit výkon při spuštění serializace XML při serializaci nebo deserializaci objektů z těchto typů pomocí <xref:System.Xml.Serialization.XmlSerializer>.

## <a name="prerequisites"></a>Požadavky

K provedení kroků v tomto kurzu je potřeba:

* [Sady SDK .NET core 2.1](https://www.microsoft.com/net/download) nebo novější
* Váš oblíbený editor kódu.

> [!TIP]
> Je potřeba nainstalovat editor kódu? Zkuste [sady Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!
  
## <a name="use-microsoft-xml-serializer-generator-in-a-net-core-console-application"></a>Použít Microsoft generátor serializátor XML v konzolovou aplikaci .NET Core 

Následující pokyny ukazují, jak používat generátor serializátor XML v konzolovou aplikaci .NET Core.

### <a name="create-a-net-core-console-application"></a>Vytvořte konzolovou aplikaci .NET Core

Otevřete příkazový řádek a vytvořte složku s názvem *MyApp*. Přejděte do složky, kterou jste vytvořili a zadejte následující příkaz:

```console
dotnet new console
```

### <a name="add-a-reference-to-the-microsoftxmlserializergenerator-package-in-the-myapp-project"></a>Přidejte odkaz na balíček Microsoft.XmlSerializer.Generator MyApp projektu

Použití [ `dotnet add package` ](../tools//dotnet-add-package.md) příkaz pro přidání odkazu ve vašem projektu. 

Zadejte:

```console
dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
```

### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a>Ověřit si změny MyApp.csproj po přidání balíčku

Otevřete editor kódu a můžeme začít! Pořád pracujeme z *MyApp* jsme vytvořili aplikaci v adresáři.

Otevřít *MyApp.csproj* v textovém editoru.

Po spuštění [ `dotnet add package` ](../tools//dotnet-add-package.md) příkazu následující řádky se přidají do vašeho *MyApp.csproj* souboru projektu:

 ```xml
 <ItemGroup>
    <PackageReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-another-itemgroup-section-for-net-core-cli-tool-support"></a>Přidejte další část ItemGroup pro podporu nástroje rozhraní příkazového řádku .NET Core

Přidejte následující řádky za `ItemGroup` oddíl, který jsme ho zkontrolovat:

 ```xml
 <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-a-class-in-the-application"></a>Přidejte třídu v aplikaci

Otevřít *Program.cs* v textovém editoru. Přidejte třídu s názvem *MyClass* v *Program.cs*.

```csharp
public class MyClass
{
   public int Value;
}
```

### <a name="create-an-xmlserializer-for-myclass"></a>Vytvoření `XmlSerializer` pro MyClass

Přidejte následující řádek uvnitř *hlavní* k vytvoření `XmlSerializer` pro MyClass:

```csharp
var serializer = new System.Xml.Serialization.XmlSerializer(typeof(MyClass));
```

### <a name="build-and-run-the-application"></a>Sestavení a spuštění aplikace

Pořád ještě uvnitř *MyApp* složky, spusťte aplikaci prostřednictvím [ `dotnet run` ](../tools/dotnet-run.md) a automaticky načte a používá předem generovaného serializátory za běhu.

Zadejte následující příkaz v okně konzoly:

```console
$ dotnet run
```

> [!NOTE]
> [`dotnet run`](../tools/dotnet-run.md) volání [ `dotnet build` ](../tools/dotnet-build.md) zajistit, aby se sestavily cíle sestavení a poté zavolá `dotnet <assembly.dll>` spustit cílovou aplikaci.

> [!IMPORTANT]
> Příkazy a postupy v tomto kurzu ke spuštění aplikace se používají pouze během vývoje. Jakmile budete připraveni k nasazení své aplikace, podívejte se na různé [strategie nasazení](../deploying/index.md) pro aplikace .NET Core a [ `dotnet publish` ](../tools/dotnet-publish.md) příkazu.

Pokud všechno proběhne úspěšně, sestavení s názvem *MyApp.XmlSerializers.dll* se generuje ve výstupní složce. 

Blahopřejeme! máte jen:
> [!div class="checklist"]
> * Vytvoření .NET Core aplikace.
> * Přidat odkaz na balíček Microsoft.XmlSerializer.Generator.
> * Upravit vaše MyApp.csproj přidat závislosti.
> * Přidat třídu a objektu XmlSerializer.
> * Vytvořené a byla aplikace spuštěná.

## <a name="related-resources"></a>Související prostředky

* [Představení serializace XML](../../standard/serialization/introducing-xml-serialization.md)
* [Postupy: Serializace pomocí třídy XmlSerializer (C#)](../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
* [Postupy: Serializace pomocí třídy XmlSerializer (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)