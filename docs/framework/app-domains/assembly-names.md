---
title: Názvy sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 8f8c2c90-f15d-400e-87e7-a757e4f04d0e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e1ab9609fe6b2c1e232f188db8306fc05828285
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744132"
---
# <a name="assembly-names"></a>Názvy sestavení
Název sestavení je uložená v metadatech a má významný dopad na rozsah sestavení a používat jiná aplikace. Sestavení se silným názvem má plně kvalifikovaný název, který obsahuje název sestavení, jazykovou verzi, veřejný klíč a číslo verze. To se často označuje jako zobrazovaný název a pro načíst sestavení můžete získat pomocí <xref:System.Reflection.Assembly.FullName%2A> vlastnost.  
  
 Modul runtime používá tuto informaci k vyhledání sestavení a rozlišit ho od ostatních sestavení se stejným názvem. Například sestavení se silným názvem názvem `myTypes` může mít následující plně kvalifikovaný název:  
  
```  
myTypes, Version=1.0.1234.0, Culture=en-US, PublicKeyToken=b77a5c561934e089c, ProcessorArchitecture=msil  
```  
  
> [!NOTE]
>  Architektura procesoru se přidá k identitě sestavení v rozhraní .NET Framework verze 2.0, aby specifické pro procesor verze sestavení. Můžete vytvořit verze sestavení, jehož identita se liší pouze pomocí architekturu procesoru, například verze specifické pro procesor 32bitové a 64bitové verze. Architektura procesoru není nutné pro silné názvy. Další informace naleznete v tématu <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=nameWithType>.  
  
 V tomto příkladu plně kvalifikovaný název znamená, že `myTypes` sestavení se silným názvem pomocí tokenu veřejného klíče, má hodnota jazykové verze pro angličtinu a má číslo verze 1.0.1234.0. Jeho architektura procesoru je "msil", což znamená, že bude v běhu (JIT)-zkompilovat kód 32bitový nebo 64bitový kód v závislosti na operačním systému a procesoru.  
  
 Kód, který požaduje typy v sestavení musí použít plně kvalifikovaný název. Tomu se říká plně kvalifikovaný vazby. Částečné vazby, která určuje jenom název sestavení, není povolena při odkazování na sestavení v rozhraní .NET Framework.  
  
 Všechny odkazy na sestavení pro sestavení, která tvoří rozhraní .NET Framework musí také obsahovat plně kvalifikovaný název sestavení. Například k odkazování sestavení System.Data rozhraní .NET Framework pro verzi 1.0 by mělo zahrnovat:  
  
```  
System.data, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
```  
  
 Všimněte si, že verze odpovídá číslo verze všech sestavení rozhraní .NET Framework, která jsou součástí rozhraní .NET Framework verze 1.0. Pro sestavení rozhraní .NET Framework hodnota jazykové verze je vždy neutrální a veřejný klíč je stejný jako v předchozím příkladu.  
  
 Pokud chcete přidat odkaz na sestavení v konfiguračním souboru nastavit naslouchací proces trasování, například bude zahrnovat plně kvalifikovaný název sestavení rozhraní .NET Framework systému:  
  
```xml  
<add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
```  
  
> [!NOTE]
>  Modul runtime názvy sestavení považuje velká a malá písmena, při vytváření vazby k sestavení, ale zachová jakoukoli velikost písmen se používá v názvu sestavení. Několik nástrojů v [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] zpracování názvy sestavení jako malá a velká písmena. Nejlepších výsledků dosáhnete spravujte názvy sestavení, jako kdyby byly malá a velká písmena.  
  
## <a name="naming-application-components"></a>Pojmenování součásti aplikace  
 Modul runtime nebere v úvahu názvu souboru při určování identity sestavení. Identita sestavení, která obsahuje název sestavení, verzi, jazykovou verzi a silným názvem, musí být jasná modulu runtime.  
  
 Například pokud máte sestavení nazvané myAssembly.exe, který odkazuje na sestavení nazvané myAssembly.dll, vazba dojde k správně Pokud spustíte myAssembly.exe. Ale pokud jiná aplikace spouští myAssembly.exe pomocí metody <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType>, modul runtime určuje, že "myAssembly" už je načtený, když myAssembly.exe žádá vazbu na "myAssembly." V takovém případě myAssembly.dll nikdy načtena. Protože myAssembly.exe neobsahuje požadovaný typ <xref:System.TypeLoadException> dojde.  
  
 K tomuto problému nedošlo, zajistěte, aby, sestavení, které tvoří vaši aplikaci mají stejný název sestavení nebo sestavení se stejným názvem umístit do různých adresářů.  
  
> [!NOTE]
>  Když vložíte sestavení se silným názvem v globální mezipaměti sestavení, název souboru sestavení musí odpovídat název sestavení (včetně není příponu názvu souboru, jako je například .exe nebo .dll). Například pokud je název souboru sestavení myAssembly.dll, název sestavení musí být myAssembly. Soukromá sestavení nasadit jenom v kořenovém adresáři aplikace může mít název sestavení, který se liší od názvu souboru.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Určení plně kvalifikovaného názvu sestavení](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
 [Vytváření sestavení](../../../docs/framework/app-domains/create-assemblies.md)  
 [Sestavení se silným názvem](../../../docs/framework/app-domains/strong-named-assemblies.md)  
 [Globální mezipaměť sestavení](../../../docs/framework/app-domains/gac.md)  
 [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md)
