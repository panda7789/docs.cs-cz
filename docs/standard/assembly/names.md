---
title: Názvy sestavení
ms.date: 08/19/2019
helpviewer_keywords:
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 8f8c2c90-f15d-400e-87e7-a757e4f04d0e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 22e35450460436e164db922fce76a53c437f6bdf
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835321"
---
# <a name="assembly-names"></a>Názvy sestavení
Název sestavení je uložen v metadatech a má významný dopad na rozsah sestavení a použití aplikací. Sestavení se silným názvem má plně kvalifikovaný název, který obsahuje název, jazykovou verzi, veřejný klíč a číslo verze sestavení. To se často označuje jako zobrazované jméno a pro načtená sestavení lze získat pomocí vlastnosti <xref:System.Reflection.Assembly.FullName%2A>.  
  
 Modul runtime používá tyto informace k vyhledání sestavení a jeho odlišení od ostatních sestavení se stejným názvem. Například sestavení se silným názvem s názvem `myTypes` může mít následující plně kvalifikovaný název:  
  
```  
myTypes, Version=1.0.1234.0, Culture=en-US, PublicKeyToken=b77a5c561934e089c, ProcessorArchitecture=msil  
```  
  
> [!NOTE]
> Do identity sestavení v .NET Framework verze 2,0 se přidá architektura procesoru, aby se povolily verze sestavení specifické pro procesor. Můžete vytvořit verze sestavení, jehož identita se liší pouze architekturou procesoru, například 32-bit a 64-bit specifických verzí procesoru. Architektura procesoru není pro silné názvy nutná. Další informace najdete v tématu <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=nameWithType>.  
  
 V tomto příkladu plně kvalifikovaný název označuje, že `myTypes` sestavení má silný název s tokenem veřejného klíče, má hodnotu jazykové verze pro jazyk US English a má číslo verze 1.0.1234.0. Jeho architektura procesoru je "MSIL", což znamená, že bude za běhu (JIT) zkompilován do 32 bitového kódu nebo 64 kódu v závislosti na operačním systému a procesoru.  
  
 Kód, který požaduje typy v sestavení, musí používat plně kvalifikovaný název sestavení. Tato metoda se nazývá plně kvalifikovaná vazba. Částečná vazba, která určuje pouze název sestavení, není povolena při odkazování na sestavení v .NET Framework.  
  
 Všechny odkazy na sestavení, které tvoří .NET Framework, musí také obsahovat plně kvalifikovaný název sestavení. Například odkaz na sestavení System. data .NET Framework pro verzi 1,0 by zahrnoval:  
  
```  
System.data, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
```  
  
 Všimněte si, že verze odpovídá číslu verze všech .NET Framework sestavení, která byla dodávána s .NET Framework verze 1,0. Pro .NET Framework sestavení je hodnota jazykové verze vždycky neutrální a veřejný klíč je stejný, jak je uvedeno v předchozím příkladu.  
  
 Chcete-li například přidat odkaz na sestavení do konfiguračního souboru pro nastavení naslouchacího procesu trasování, zahrnete plně kvalifikovaný název systémového .NET Framework sestavení:  
  
```xml  
<add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
```  
  
> [!NOTE]
> Modul runtime považuje názvy sestavení za nerozlišování velkých a malých písmen při vytváření vazby na sestavení, ale zachová bez ohledu na případ použití v názvu sestavení. Několik nástrojů v Windows SDK zpracovává názvy sestavení při rozlišování velkých a malých písmen. Pro dosažení nejlepších výsledků spravujte názvy sestavení, jako by se jednalo o velká a malá písmena.  
  
## <a name="name-application-components"></a>Pojmenovat součásti aplikace  
 Modul runtime při určování identity sestavení nebere v úvahu název souboru. Identita sestavení, která se skládá z názvu sestavení, verze, jazykové verze a silného názvu, musí být pro modul runtime nejasná.  
  
 Například pokud máte sestavení s názvem *MyAssembly. exe* , které odkazuje na sestavení s názvem *MyAssembly. dll*, vazba proběhne správně, pokud spustíte *MyAssembly. exe*. Pokud však jiná aplikace provádí *MyAssembly. exe* pomocí metody <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType>, modul runtime určí, že `myAssembly` je již načteno, když *MyAssembly. exe* požaduje vazbu na `myAssembly`. V tomto případě není *MyAssembly. dll* nikdy načtena. Protože *MyAssembly. exe* neobsahuje požadovaný typ, dojde k <xref:System.TypeLoadException>.  
  
 Chcete-li se tomuto problému vyhnout, ujistěte se, že sestavení, která tvoří vaši aplikaci, nemají stejný název sestavení nebo umísťují sestavení se stejným názvem do různých adresářů.  
  
> [!NOTE]
> Pokud v .NET Framework umístíte sestavení se silným názvem do globální mezipaměti sestavení (GAC), název souboru sestavení musí odpovídat názvu sestavení, včetně přípony názvu souboru, například *. exe* nebo *. dll*. Například pokud název souboru sestavení je *MyAssembly. dll*, název sestavení musí být `myAssembly`. Soukromá sestavení nasazená pouze v kořenovém adresáři aplikace mohou mít název sestavení, který se liší od názvu souboru.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: určení plně kvalifikovaného názvu sestavení](find-fully-qualified-name.md)
- [Vytváření sestavení](create.md)
- [Sestavení se silným názvem](strong-named.md)
- [Globální mezipaměť sestavení](../../framework/app-domains/gac.md)
- [Způsob, jakým modul runtime vyhledává sestavení](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [Program se sestaveními](program.md)
