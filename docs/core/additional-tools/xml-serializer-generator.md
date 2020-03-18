---
title: Generátor serializátorů XML společnosti Microsoft
description: Přehled generátoru serializátorů XML společnosti Microsoft. Generátor serializátorů XML slouží ke generování sestavení serializace XML pro typy obsažené v projektu.
author: mlacouture
ms.date: 01/19/2017
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 094dd1227033e167050ad73121b3005a592a0ae4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714525"
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a>Použití generátoru serializátorů jazyka Microsoft XML v jádru .NET Core

Tento kurz vás naučí používat generátor serializátorů XML společnosti Microsoft v aplikaci C# .NET Core. V průběhu tohoto kurzu se naučíte:

> [!div class="checklist"]
>
> - Vytvoření aplikace v .NET Core
> - Přidání odkazu do balíčku Microsoft.XmlSerializer.Generator
> - Úprava souboru MyApp.csproj a přidání závislostí
> - Přidání třídy a objektu XmlSerializer
> - Sestavení a spuštění aplikace

Podobně jako [generátor serializátorů XML (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) pro rozhraní .NET Framework je [balíček Microsoft.XmlSerializer.Generator NuGet](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) ekvivalentní pro projekty .NET Core a .NET Standard. Vytvoří sestavení serializace XML pro typy obsažené v sestavení ke zlepšení výkonu při spuštění serializace XML při <xref:System.Xml.Serialization.XmlSerializer>serializaci nebo deserializaci objektů těchto typů pomocí .

## <a name="prerequisites"></a>Požadavky

Pro absolvování tohoto kurzu potřebujete:

- [Sada .NET Core 2.1 SDK](https://dotnet.microsoft.com/download) nebo novější.
- Váš oblíbený editor kódu.

> [!TIP]
> Potřebujete nainstalovat editor kódu? Vyzkoušejte [visual studio!](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

## <a name="use-microsoft-xml-serializer-generator-in-a-net-core-console-application"></a>Použití generátoru serializátorů jazyka Microsoft XML v aplikaci konzoly .NET Core

Následující pokyny ukazují, jak používat generátor serializátorů XML v aplikaci konzoly .NET Core.

### <a name="create-a-net-core-console-application"></a>Vytvoření konzolové aplikace .NET Core

Otevřete příkazový řádek a vytvořte složku s názvem *MyApp*. Přejděte do složky, kterou jste vytvořili, a zadejte následující příkaz:

```dotnetcli
dotnet new console
```

### <a name="add-a-reference-to-the-microsoftxmlserializergenerator-package-in-the-myapp-project"></a>Přidání odkazu na balíček Microsoft.XmlSerializer.Generator v projektu MyApp

Pomocí [`dotnet add package`](../tools//dotnet-add-package.md) příkazu přidejte odkaz v projektu.

Zadejte:

```dotnetcli
dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
```

### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a>Ověření změn myapp.csproj po přidání balíčku

Otevřete editor kódu a začneme! Stále pracujeme z adresáře *MyApp,* do kterýjsme aplikaci vytvořili.

Otevřete *myApp.csproj* v textovém editoru.

Po spuštění [`dotnet add package`](../tools//dotnet-add-package.md) příkazu se do souboru projektu *MyApp.csproj* přidají následující řádky:

 ```xml
 <ItemGroup>
    <PackageReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-another-itemgroup-section-for-net-core-cli-tool-support"></a>Přidání další části Skupiny položek pro podporu nástroje .NET Core CLI Tool

Za `ItemGroup` oddíl, který jsme zkontrolovali, přidejte následující řádky:

 ```xml
 <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-a-class-in-the-application"></a>Přidání třídy do aplikace

Otevřete *Program.cs* v textovém editoru. Přidejte třídu s názvem *MyClass* do *Program.cs*.

```csharp
public class MyClass
{
   public int Value;
}
```

### <a name="create-an-xmlserializer-for-myclass"></a>Vytvořit `XmlSerializer` pro MyClass

Přidejte následující *Main* řádek uvnitř `XmlSerializer` Main pro vytvoření pro MyClass:

```csharp
var serializer = new System.Xml.Serialization.XmlSerializer(typeof(MyClass));
```

### <a name="build-and-run-the-application"></a>Sestavení a spuštění aplikace

Stále ve složce *MyApp,* [`dotnet run`](../tools/dotnet-run.md) spusťte aplikaci přes a automaticky načte a používá pre-generované serializers za běhu.

Do okna konzole zadejte následující příkaz:

```dotnetcli
dotnet run
```

> [!NOTE]
> [`dotnet run`](../tools/dotnet-run.md)volání [`dotnet build`](../tools/dotnet-build.md) zajistit, že cíle sestavení byly vytvořeny `dotnet <assembly.dll>` a potom volá ke spuštění cílové aplikace.

> [!IMPORTANT]
> Příkazy a kroky uvedené v tomto kurzu ke spuštění aplikace se používají pouze v době vývoje. Až budete připraveni k nasazení aplikace, podívejte se na různé [strategie nasazení](../deploying/index.md) [`dotnet publish`](../tools/dotnet-publish.md) pro aplikace .NET Core a příkaz.

Pokud vše úspěšné, sestavení s názvem *MyApp.XmlSerializers.dll* je generovánve výstupní složce.

Blahopřejeme! Máte jen:
> [!div class="checklist"]
>
> - Byla vytvořena aplikace .NET Core.
> - Byl přidán odkaz na balíček Microsoft.XmlSerializer.Generator.
> - Upravil myApp.csproj přidat závislosti.
> - Přidána třída a XmlSerializer.
> - Byla vytvořena a spuštěna aplikace.

## <a name="related-resources"></a>Související prostředky

- [Představení serializace XML](../../standard/serialization/introducing-xml-serialization.md)
- [Jak serializovat pomocí XmlSerializer (C#)](../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
- [Postup: Serializace pomocí xmlserializeru (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
