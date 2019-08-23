---
title: Element <loadFromRemoteSources>
ms.date: 05/24/2018
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2268d07fb643621c944ef9bf561156b5332aaafc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920708"
---
# <a name="loadfromremotesources-element"></a>\<loadFromRemoteSources – element >
Určuje, zda mají být sestavení načtena ze vzdálených zdrojů udělena plná důvěryhodnost v .NET Framework 4 a novějších.
  
> [!NOTE]
> Pokud jste byli přesměrováni na tento článek z důvodu chybové zprávy v seznamu chyb projektu sady Visual Studio nebo chyba sestavení, přečtěte [si téma How to: Použijte sestavení z webu v aplikaci Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).  
  
 \<> Konfigurace  
\<> modulu runtime  
\<loadFromRemoteSources>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<loadFromRemoteSources    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, jestli má být sestavení, které je načtené ze vzdáleného zdroje, udělené plné důvěryhodnosti.|  
  
## <a name="enabled-attribute"></a>povolený atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|`false`|Neudělujete úplný vztah důvěryhodnosti aplikacím ze vzdálených zdrojů. Toto nastavení je výchozí.|  
|`true`|Udělte úplný vztah důvěryhodnosti aplikacím ze vzdálených zdrojů.|  
  
### <a name="child-elements"></a>Podřízené prvky  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené prvky  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
  
## <a name="remarks"></a>Poznámky

Pokud se v .NET Framework 3,5 a starších verzích načte sestavení ze vzdáleného umístění, kód v sestavení běží v částečném vztahu důvěryhodnosti se sadou udělení, která závisí na zóně, ze které je načtena. Například pokud načtete sestavení z webu, je načteno do zóny Internet a udělena sada oprávnění Internet. Jinými slovy se spustí v internetovém prostoru.

Počínaje .NET Framework 4 jsou zásady zabezpečení přístupu kódu (CAS) zakázané a sestavení se načítají v úplném vztahu důvěryhodnosti. Obvykle to udělí úplný vztah důvěryhodnosti k sestavením načteným pomocí <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metody, která dříve byla izolovaného prostoru (sandbox). Aby se zabránilo tomu, možnost spouštění kódu v sestaveních načtených ze vzdáleného zdroje je ve výchozím nastavení zakázána. Ve výchozím nastavení platí, že pokud se pokusíte načíst vzdálené sestavení <xref:System.IO.FileLoadException> , bude vyvolána zpráva s výjimkou, například následující:

```text
System.IO.FileNotFoundException: Could not load file or assembly 'file:assem.dll' or one of its dependencies. Operation is not supported. 
(Exception from HRESULT: 0x80131515)
File name: 'file:assem.dll' ---> 
System.NotSupportedException: An attempt was made to load an assembly from a network location which would have caused the assembly 
to be sandboxed in previous versions of the .NET Framework. This release of the .NET Framework does not enable CAS policy by default, 
so this load may be dangerous. If this load is not intended to sandbox the assembly, please enable the loadFromRemoteSources switch. 
```

Chcete-li načíst sestavení a spustit jeho kód, je nutné buď:

- Explicitní vytvoření izolovaného prostoru pro sestavení (viz [How to: Spustit částečně důvěryhodný kód v izolovaném](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)prostoru (sandbox)).

- Spusťte kód sestavení v úplném vztahu důvěryhodnosti. To provedete tak, `<loadFromRemoteSources>` že nakonfigurujete prvek. Umožňuje určit, že sestavení, která běží v částečném vztahu důvěryhodnosti v dřívějších verzích .NET Framework nyní běží v úplném vztahu důvěryhodnosti v .NET Framework 4 a novějších verzích.

> [!IMPORTANT]
> Pokud by sestavení nemělo běžet v úplném vztahu důvěryhodnosti, nenastavte tento prvek konfigurace. Místo toho vytvořte izolovaný prostor <xref:System.AppDomain> , ve kterém chcete sestavení načíst.

`enabled` Atribut`<loadFromRemoteSources>` pro element je platný pouze v případě, že je zakázáno zabezpečení přístupu kódu (CAS). Ve výchozím nastavení jsou zásady CAS zakázané v .NET Framework 4 a novějších verzích. Pokud nastavíte `enabled` na `true`, jsou vzdálená sestavení udělena plná důvěryhodnost.

Pokud `enabled` není nastaven na `true`, <xref:System.IO.FileLoadException> je vyvolána jedna z následujících podmínek:

- Chování izolovaného prostoru aktuální domény se liší od chování v .NET Framework 3,5. To vyžaduje, aby byly zásady CAS zakázané a aby aktuální doména nebyla v izolovaném prostoru.

- Načtené sestavení není ze `MyComputer` zóny.

Nastavení elementu pro `true` zabránění vyvolání této výjimky. `<loadFromRemoteSources>` Umožňuje určit, že se nespoléháte na modul CLR (Common Language Runtime) k izolovanému prostoru pro načtená sestavení pro zabezpečení a že může být povoleno provádět v úplném vztahu důvěryhodnosti.

## <a name="notes"></a>Poznámky

- V .NET Framework 4,5 a novějších verzích jsou sestavení v místních síťových sdílených složkách ve výchozím nastavení spouštěna v úplném vztahu důvěryhodnosti. není nutné povolit `<loadFromRemoteSources>` element.

- Pokud byla aplikace zkopírována z webu, je označena systémem Windows jako webová aplikace, a to i v případě, že se nachází v místním počítači. Toto označení můžete změnit změnou jeho vlastností souboru, nebo můžete použít `<loadFromRemoteSources>` element pro udělení úplného vztahu důvěryhodnosti sestavení. Alternativně můžete použít <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> metodu pro načtení místního sestavení, které má operační systém označen jako načtený z webu.

- Můžete se dostat <xref:System.IO.FileLoadException> do aplikace, která běží v aplikaci Virtual PC v systému Windows. K tomu může dojít při pokusu o načtení souboru z propojených složek v hostitelském počítači. Může k tomu dojít i v případě, že se pokusíte načíst soubor ze složky propojené přes [službu Vzdálená plocha](https://go.microsoft.com/fwlink/?LinkId=182775) (Terminálová služba). Chcete-li výjimku zabránit, `enabled` nastavte `true`na.

## <a name="configuration-file"></a>Konfigurační soubor

Tento element se obvykle používá v konfiguračním souboru aplikace, ale lze jej použít v jiných konfiguračních souborech v závislosti na kontextu. Další informace najdete v článku [více implicitních použití zásad CAS: loadFromRemoteSources](https://go.microsoft.com/fwlink/p/?LinkId=266839) na blogu zabezpečení .NET.  

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak udělit úplný vztah důvěryhodnosti k sestavením načteným ze vzdálených zdrojů.

```xml
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```

## <a name="see-also"></a>Viz také:

- [Více implicitních použití zásad CAS: loadFromRemoteSources](https://go.microsoft.com/fwlink/p/?LinkId=266839)
- [Postupy: Spustit částečně důvěryhodný kód v izolovaném prostoru](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
