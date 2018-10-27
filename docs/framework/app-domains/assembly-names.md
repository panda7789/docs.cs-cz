---
title: Názvy sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 8f8c2c90-f15d-400e-87e7-a757e4f04d0e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6447593ba81e4512afaf2b5798fcec00b755e63c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50184773"
---
# <a name="assembly-names"></a>Názvy sestavení
Název sestavení je uložená v metadatech a má významný dopad na rozsah sestavení a používat aplikace. Sestavení se silným názvem je plně kvalifikovaný název, který obsahuje název sestavení, jazykové verze, veřejného klíče a číslo verze. To se často označuje jako zobrazovaný název a pro načtená sestavení lze získat pomocí <xref:System.Reflection.Assembly.FullName%2A> vlastnost.  
  
 Modul runtime používá tyto informace k nalezení sestavení a odlišují ji od ostatních sestavení se stejným názvem. Například sestavení se silným názvem názvem `myTypes` může mít tento plně kvalifikovaný název:  
  
```  
myTypes, Version=1.0.1234.0, Culture=en-US, PublicKeyToken=b77a5c561934e089c, ProcessorArchitecture=msil  
```  
  
> [!NOTE]
>  Architektura procesoru je přidána do identity sestavení v rozhraní .NET Framework verze 2.0, aby specifické pro procesor verze sestavení. Můžete vytvořit sestavení, jehož identita se liší pouze ve architekturu procesoru, například verze specifické pro procesor 32bitové a 64bitové verze. Architektura procesoru není vyžadována pro silné názvy. Další informace naleznete v tématu <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=nameWithType>.  
  
 V tomto příkladu je plně kvalifikovaný název označuje, že `myTypes` sestavení se silným názvem pomocí tokenu veřejného klíče, má hodnota jazykové verze pro angličtinu a má číslo verze 1.0.1234.0. Jeho architektuře procesoru je "msil", což znamená, že bude just-in-time (JIT)-zkompilováno do 32bitového kódu nebo 64bitového kódu v závislosti na operačním systému a procesoru.  
  
 Kód, který požaduje typy v sestavení, musíte použít plně kvalifikovaný název. Tomu se říká plně kvalifikovaný vazby. Částečné vazby, který určuje pouze název sestavení, není povoleno při odkazování na sestavení v rozhraní .NET Framework.  
  
 Všechny odkazy na sestavení pro sestavení, která tvoří rozhraní .NET Framework také musí obsahovat plně kvalifikovaný název sestavení. Například odkazovat na sestavení System.Data rozhraní .NET Framework verze 1.0 zahrnuje:  
  
```  
System.data, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
```  
  
 Všimněte si, že verze odpovídá verzi počet všechna sestavení rozhraní .NET Framework, která jsou součástí rozhraní .NET Framework verze 1.0. Pro sestavení rozhraní .NET Framework je vždy neutrální jazykovou verzi hodnota a veřejný klíč je stejný, jak je znázorněno v příkladu výše.  
  
 Chcete-li přidat odkaz na sestavení v konfiguračním souboru nastavit naslouchací proces trasování, například bude zahrnovat plně kvalifikovaný název systému sestavení rozhraní .NET Framework:  
  
```xml  
<add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
```  
  
> [!NOTE]
>  Modul runtime považuje za názvy sestavení velkých a malých písmen při vytváření vazby na sestavení, ale zachová v názvu sestavení se používá jakoukoli velikost písmen. Několik nástrojů [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] zpracování názvy sestavení jako malá a velká písmena. Nejlepších výsledků dosáhnete spravujte názvy sestavení, jako by byly malá a velká písmena.  
  
## <a name="naming-application-components"></a>Pojmenování součásti aplikace  
 Modul runtime nebere v úvahu názvu souboru při určování identity sestavení. Identitu sestavení, který se skládá z názvu sestavení, verzi, jazykovou verzi a silným názvem, musí být jasný modulu runtime.  
  
 Například pokud máte sestavení nazvané myAssembly.exe, který odkazuje na sestavení nazvané myAssembly.dll, vazba v případě správně spustit myAssembly.exe. Nicméně pokud jiná aplikace provádí pomocí metody myAssembly.exe <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType>, modul runtime určuje, že "myAssembly" je již načtena, když myAssembly.exe požádá o vazbu k "myAssembly." V takovém případě myAssembly.dll vůbec nenačetl. Protože myAssembly.exe neobsahuje požadovaný typ <xref:System.TypeLoadException> vyvolá.  
  
 K tomuto problému vyhnout, ujistěte se, že sestavení, které tvoří vaši aplikaci se stejným názvem sestavení nebo sestavení se stejným názvem umístit do různých adresářích.  
  
> [!NOTE]
>  Když vložíte sestavení se silným názvem do globální mezipaměti sestavení, název souboru sestavení musí odpovídat názvu sestavení (nezahrnuje příponu názvu souboru, jako je například .exe nebo .dll). Například pokud je název souboru sestavení myAssembly.dll, musí být název sestavení myAssembly. Soukromá sestavení, které jsou nasazeny pouze v kořenovém adresáři aplikace může mít název sestavení, které se liší od názvu souboru.  
  
## <a name="see-also"></a>Viz také  
- [Postupy: Určení plně kvalifikovaného názvu sestavení](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
- [Vytváření sestavení](../../../docs/framework/app-domains/create-assemblies.md)  
- [Sestavení se silným názvem](../../../docs/framework/app-domains/strong-named-assemblies.md)  
- [Globální mezipaměť sestavení](../../../docs/framework/app-domains/gac.md)  
- [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
- [Programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md)
