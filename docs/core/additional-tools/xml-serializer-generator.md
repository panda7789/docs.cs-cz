---
title: Pomocí generátoru serializátor Microsoft XML na .NET Core
description: Přehled generátor serializátor XML společnosti Microsoft.
author: mlacouture
ms.author: johalex
ms.date: 01/19/2017
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 98d85821784757db903c97e240c55a3d7bb656d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a>Pomocí generátoru serializátor Microsoft XML na .NET Core

V tomto kurzu se naučíte, jak používat generátor serializátor XML společnosti Microsoft v aplikaci C# .NET Core. V průběhu tohoto kurzu se seznámíte:

> [!div class="checklist"]
> * Jak vytvořit aplikaci .NET Core
> * Jak přidat odkaz na balíček Microsoft.XmlSerializer.Generator
> * Úprava vaší MyApp.csproj přidat závislosti
> * Přidání třídy a třídy XmlSerializer
> * Postup vytvoření a spuštění aplikace 

Jako [generátor serializátor Xml (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) pro rozhraní .NET Framework [balíček Microsoft.XmlSerializer.Generator NuGet](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) je ekvivalentem pro projekty .NET Core a .NET Standard. Vytvoří sestavení serializace XML pro typy, které jsou součástí sestavení, které chcete zvýšit výkon při spuštění serializace XML při serializaci nebo zrušte serializaci objektů těchto typů pomocí <xref:System.Xml.Serialization.XmlSerializer>.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto kurzu:

* Nainstalujte [.NET Core SDK 2.1.3 nebo novější](https://www.microsoft.com/net/download)
* Pokud jste to ještě neudělali, nainstalujte editor vaše oblíbené kódu.

> [!TIP]
> Je potřeba nainstalovat editor kódu? Zkuste [sady Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!
  
## <a name="use-microsoft-xml-serializer-generator-in-a-net-core-console-application"></a>Použít Microsoft XML serializátor generátor v konzolové aplikaci .NET Core 

Následující pokyny ukazují, jak používat generátor serializátor XML v konzolové aplikaci .NET Core.

### <a name="create-a-net-core-console-application"></a>Vytvoření aplikace konzoly .NET Core

Otevřete příkazový řádek a vytvořte složku s názvem *Moje aplikace*. Přejděte do složky, kterou jste vytvořili a zadejte následující příkaz:

```console
dotnet new console
```

### <a name="add-a-reference-to-the-microsoftxmlserializergenerator-package-in-the-myapp-project"></a>Přidat odkaz na balíček Microsoft.XmlSerializer.Generator v projektu Moje aplikace

Použití [ `dotnet add package` ](../tools//dotnet-add-package.md) příkaz Přidat odkaz ve vašem projektu. 

Typ:
 
 ```console
 dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
 ```
 
### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a>Ověřit si změny MyApp.csproj po přidání balíčku

Otevřete editor kódu a můžeme začít! Stále pracujeme z *Moje aplikace* jsme vytvořili aplikaci v adresáři.

Otevřete *MyApp.csproj* v textovém editoru.

Po spuštění [ `dotnet add package` ](../tools//dotnet-add-package.md) příkazu, jsou přidány následující řádky do vaší *MyApp.csproj* soubor projektu:

 ```xml
 <ItemGroup>
    <PackageReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```
 
### <a name="add-another-itemgroup-section-for-net-core-cli-tool-support"></a>Přidat jinou část ItemGroup pro podporu rozhraní .NET Core rozhraní příkazového řádku nástroje
 
 Přidejte následující řádky po `ItemGroup` oddíl, který jsme prověřovány:
 
 ```xml
 <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```
 
### <a name="add-a-class-in-the-application"></a>Přidání třídy v aplikaci

Otevřete *Program.cs* v textovém editoru. Přidejte třídu s názvem *MyClass* v *Program.cs*.

```csharp
public class MyClass
{
   public int Value;
}
```

### <a name="create-an-xmlserializer-for-myclass"></a>Vytvoření `XmlSerializer` pro MyClass

Přidejte následující řádek uvnitř *hlavní* vytvořit `XmlSerializer` pro MyClass:

```csharp
var serializer = new System.Xml.Serialization.XmlSerializer(typeof(MyClass));
```

### <a name="build-and-run-the-application"></a>Sestavení a spuštění aplikace

Stále ještě v *Moje aplikace* složky, spusťte aplikaci prostřednictvím [ `dotnet run` ](../tools/dotnet-run.md) a automaticky načte a používá předem vygenerovaná serializátorů za běhu.

Zadejte následující příkaz v okně konzoly:

 ```console
 $ dotnet run
 ```
> [!NOTE]
> [`dotnet run`](../tools/dotnet-run.md) volání [ `dotnet build` ](../tools/dotnet-build.md) zajistit, aby sestavení, které se sestavily cíle a poté zavolá `dotnet <assembly.dll>` ke spuštění cílová aplikace.

> [!IMPORTANT]
> Příkazy a postupy v tomto kurzu ke spuštění vaší aplikace se používají pouze dobu vývoj. Jakmile budete připraveni k nasazení své aplikace, prohlédněte si různými [strategie nasazení](../deploying/index.md) pro aplikace .NET Core a [ `dotnet publish` ](../tools/dotnet-publish.md) příkaz.

Pokud všechno proběhne úspěšně, sestavení s názvem *MyApp.XmlSerializers.dll* se generuje ve výstupní složce. 



Blahopřejeme! máte právě:
> [!div class="checklist"]
> * Vytvořit .NET Core aplikace.
> * Přidat odkaz na balíček Microsoft.XmlSerializer.Generator.
> * Upravit vaše MyApp.csproj přidat závislosti.
> * Přidání třídy a XmlSerializer.
> * Vytvořené a spustil aplikaci. 

## <a name="related-resources"></a>Související informační zdroje

* [Představení serializace XML](../../standard/serialization/introducing-xml-serialization.md)
* [Postupy: serializace pomocí třídy XmlSerializer (C#)](../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
* [Postupy: serializace pomocí třídy XmlSerializer (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
