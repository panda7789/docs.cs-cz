---
title: Element <loadFromRemoteSources>
ms.date: 05/24/2018
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
ms.openlocfilehash: a0dcffe378cdd09de0fbd8f0a6ef0635c033fd9c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154059"
---
# <a name="loadfromremotesources-element"></a>\<loadFromRemoteSources> element
Určuje, zda mají být sestavením načteným ze vzdálených zdrojů udělena úplná důvěryhodnost v rozhraní .NET Framework 4 a novějších.
  
> [!NOTE]
> Pokud jste byli přesměrováni na tento článek z důvodu chybové zprávy v seznamu chyb projektu sady Visual Studio nebo chyby sestavení, [přečtěte si téma Postup: Použití sestavení z webu v sadě Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).  
  
[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>za běhu**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<loadFromRemoteSources>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<loadFromRemoteSources
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a prvky
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda má být sestavení načtené ze vzdáleného zdroje udělenúplný vztah důvěryhodnosti.|  
  
## <a name="enabled-attribute"></a>povolený atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Neudělujte úplný vztah důvěryhodnosti aplikacím ze vzdálených zdrojů. Toto nastavení je výchozí.|  
|`true`|Udělte plnou důvěryhodnost aplikacím ze vzdálených zdrojů.|  
  
### <a name="child-elements"></a>Podřízené prvky  
 Žádné.  
  
### <a name="parent-elements"></a>Nadřazené prvky  
  
|Element|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
  
## <a name="remarks"></a>Poznámky

V rozhraní .NET Framework 3.5 a starších verzích pokud načtete sestavení ze vzdáleného umístění, kód v sestavení běží v částečném vztahu důvěryhodnosti s grantovou sadou, která závisí na zóně, ze které je načteno. Pokud například načtete sestavení z webu, načte se do zóny Internet a bude mu udělena sada oprávnění k Internetu. Jinými slovy, provádí se v internetové izolované masivu.

Počínaje rozhraním .NET Framework 4 je zakázána zásada zabezpečení přístupu kódu (CAS) a sestavení jsou načtena v plném vztahu důvěryhodnosti. Obvykle by to udělit úplný vztah důvěryhodnosti sestavení naložené <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> s metodou, která byla dříve v izolovaném prostoru. Chcete-li tomu zabránit, je ve výchozím nastavení zakázána možnost spouštět kód v sestaveních načtených ze vzdáleného zdroje. Ve výchozím nastavení, pokud se pokusíte <xref:System.IO.FileLoadException> načíst vzdálené sestavení, a s výjimkou zprávy, jako je následující je vyvolána:

```text
System.IO.FileNotFoundException: Could not load file or assembly 'file:assem.dll' or one of its dependencies. Operation is not supported.
(Exception from HRESULT: 0x80131515)
File name: 'file:assem.dll' --->
System.NotSupportedException: An attempt was made to load an assembly from a network location which would have caused the assembly
to be sandboxed in previous versions of the .NET Framework. This release of the .NET Framework does not enable CAS policy by default,
so this load may be dangerous. If this load is not intended to sandbox the assembly, please enable the loadFromRemoteSources switch.
```

Chcete-li načíst sestavení a spustit jeho kód, musíte buď:

- Explicitně vytvořte izolovaného prostoru pro sestavení (viz [Postup: Spustit částečně důvěryhodný kód v izolovaném prostoru).](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)

- Spusťte kód sestavení v plném vztahu důvěryhodnosti. To provést konfigurací `<loadFromRemoteSources>` prvku. Umožňuje určit, že sestavení, která jsou spuštěna v částečném vztahu důvěryhodnosti v dřívějších verzích rozhraní .NET Framework, jsou nyní spuštěna v plně důvěře v rozhraní .NET Framework 4 a novějších verzích.

> [!IMPORTANT]
> Pokud by sestavení nemělo být spuštěno v plném vztahu důvěryhodnosti, nenastavujte tento konfigurační prvek. Místo toho vytvořte sandbox, <xref:System.AppDomain> ve kterém chcete načíst sestavu.

Atribut `enabled` pro `<loadFromRemoteSources>` prvek je účinný pouze v případě, že je zakázáno zabezpečení přístupu kódu (CAS). Ve výchozím nastavení je zásada CAS zakázána v rozhraní .NET Framework 4 a novějších verzích. Pokud nastavíte na `enabled` `true`, vzdálená sestavení jsou udělena plná důvěryhodnost.

Není-li `enabled` nastavena na `true`, <xref:System.IO.FileLoadException> je a vyvolána za jedné z následujících podmínek:

- Chování sandboxing aktuální domény se liší od jeho chování v rozhraní .NET Framework 3.5. To vyžaduje, aby byly zásady CAS zakázány a aktuální doména nebyla v izolovaném prostoru.

- Načtená sestava není ze `MyComputer` zóny.

Nastavení `<loadFromRemoteSources>` prvku `true` zabránit této výjimce vyvolána. Umožňuje určit, že nespoléháte na běžný jazyk runtime do izolovaného prostoru načtená sestavení pro zabezpečení a že mohou být povoleny pro spuštění v plném vztahu důvěryhodnosti.

## <a name="notes"></a>Poznámky

- V rozhraní .NET Framework 4.5 a novějších verzích jsou sestavení sdílených složek místní sítě ve výchozím nastavení plně důvěryhodná. není třeba povolit `<loadFromRemoteSources>` prvek.

- Pokud byla aplikace zkopírována z webu, je systémem Windows označena jako webová aplikace, i když je umístěna v místním počítači. Toto označení můžete změnit změnou jeho vlastností `<loadFromRemoteSources>` souboru nebo můžete prvek použít k udělení úplnédůvěryhodnosti sestavení. Alternativně můžete použít metodu <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> k načtení místního sestavení, které operační systém označil jako načtené z webu.

- Můžete získat <xref:System.IO.FileLoadException> v aplikaci, která je spuštěna v aplikaci Virtuální počítač se systémem Windows. K tomu může dojít při pokusu o načtení souboru z propojených složek v hostitelském počítači. Může k tomu dojít také při pokusu o načtení souboru ze složky propojené [prostředpou Vzdálená plocha](/windows/win32/termserv/terminal-services-portal) (Terminálová služba). Chcete-li se `enabled` vyhnout `true`výjimce, nastavte na .

## <a name="configuration-file"></a>Konfigurační soubor

Tento prvek se obvykle používá v konfiguračním souboru aplikace, ale lze jej použít v jiných konfiguračních souborech v závislosti na kontextu. Další informace naleznete v článku [Další implicitní použití zásad CAS: loadFromRemoteSources](https://docs.microsoft.com/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources) v blogu .NET Security.  

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak udělit úplný vztah důvěryhodnosti sestavením načteným ze vzdálených zdrojů.

```xml
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```

## <a name="see-also"></a>Viz také

- [Další implicitní použití zásad CAS: loadFromRemoteSources](https://docs.microsoft.com/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources)
- [Postupy: Spuštění částečně důvěryhodného kódu v izolovaném prostoru](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
