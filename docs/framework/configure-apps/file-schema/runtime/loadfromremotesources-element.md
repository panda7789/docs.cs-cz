---
title: '&lt;loadFromRemoteSources&gt; – Element'
ms.date: 05/24/2018
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a8858059159edddb4456561719c572fb9268be7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43509480"
---
# <a name="ltloadfromremotesourcesgt-element"></a>&lt;loadFromRemoteSources&gt; – element
Určuje, zda sestavení načtená ze vzdáleného zdroje by měly být udělena úplná důvěryhodnost v rozhraní .NET Framework 4 nebo novější.
  
> [!NOTE]
>  Pokud k tomuto tématu byli přesměrováni z důvodu chybovou zprávu v seznamu chyb sady Visual Studio projekt nebo sestavení chyby, přečtěte si téma [postupy: použití sestavení z webu v sadě Visual Studio](https://msdn.microsoft.com/library/d8635b63-89a0-41aa-90f4-f351b2111070).  
  
 \<Konfigurace >  
\<modul runtime >  
\<loadFromRemoteSources >  
  
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
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda sestavení, který je načten ze vzdáleného zdroje by měly být udělena úplná důvěryhodnost.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Neudělujte úplný vztah důvěryhodnosti k aplikacím ze vzdálených zdrojů. Toto nastavení je výchozí.|  
|`true`|Udělte úplný vztah důvěryhodnosti k aplikacím ze vzdálených zdrojů.|  
  
### <a name="child-elements"></a>Podřízené prvky  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené prvky  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
  
## <a name="remarks"></a>Poznámky

V rozhraní .NET Framework 3.5 a starší verze Pokud načtete sestavení ze vzdáleného umístění, spustí kód v sestavení v částečném vztahu důvěryhodnosti pomocí sady udělení, který závisí na zónu, ze které je načten. Například pokud načtete sestavení z webu, je načten do zóny Internet a udělená sada oprávnění Internetu. Jinými slovy spouští v sandboxu sítě Internet.

Od verze rozhraní .NET Framework 4, code access security (CAS) zásada je zakázána a sestavení jsou načtena v režimu plné důvěryhodnosti. Obvykle to udělit úplný vztah důvěryhodnosti k sestavení načtená <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metodu, která dříve byla v izolovaném prostoru. Chcete-li tomu zabránit, umožňuje spouštění kódu v sestavení načtená ze vzdáleného zdroje je standardně zakázáno. Ve výchozím nastavení, pokud se pokusíte načíst vzdálené sestavení <xref:System.IO.FileLoadException> se zprávou výjimky, jako je vyvolána následující výjimka:

```text
System.IO.FileNotFoundException: Could not load file or assembly 'file:assem.dll' or one of its dependencies. Operation is not supported. 
(Exception from HRESULT: 0x80131515)
File name: 'file:assem.dll' ---> 
System.NotSupportedException: An attempt was made to load an assembly from a network location which would have caused the assembly 
to be sandboxed in previous versions of the .NET Framework. This release of the .NET Framework does not enable CAS policy by default, 
so this load may be dangerous. If this load is not intended to sandbox the assembly, please enable the loadFromRemoteSources switch. 
```

Načtení sestavení a provedení jeho kód, musíte buď:

- Explicitně vytvořit izolovaný prostor pro sestavení (viz [postupy: spuštění částečně důvěryhodného kódu v izolovaném prostoru](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)).

- Spusťte sestavení kódu v režimu plné důvěryhodnosti. To provedete tím, že nakonfigurujete `<loadFromRemoteSources>` elementu. To vám umožní zadat, že sestavení, na kterých běží v částečném vztahu důvěryhodnosti v dřívějších verzích rozhraní .NET Framework nyní spustit v úplném vztahu důvěryhodnosti v rozhraní .NET Framework 4 a novější verze.

> [!IMPORTANT]
> Pokud sestavení by neměl spustit v úplném vztahu důvěryhodnosti, nenastavujte tento prvek konfigurace. Místo toho vytvořte v izolovaném prostoru <xref:System.AppDomain> ve kterých se mají načíst sestavení.

`enabled` Atribut pro `<loadFromRemoteSources>` element je účinné pouze když je zakázáno zabezpečení přístupu kódu (CAS). Ve výchozím nastavení zásady CAS zakázaná v rozhraní .NET Framework 4 a novější verze. Pokud nastavíte `enabled` k `true`, vzdálené sestavení jsou udělena úplná důvěryhodnost.

Pokud `enabled` není nastavená na `true`, <xref:System.IO.FileLoadException> je vyvolána v rámci některý z následujících podmínek:

- Chování sandboxing aktuální domény se liší od chování v rozhraní .NET Framework 3.5. To vyžaduje zásady CAS se deaktivuje a aktuální doména by se v izolovaném prostoru.

- Načítané sestavení se nenachází `MyComputer` zóny.

Nastavení `<loadFromRemoteSources>` elementu `true` brání vyvolání této výjimky. Umožňuje určit, že se spoléhá na modul common language runtime do izolovaného prostoru načtená sestavení pro zabezpečení a, může být povoleno spustit v plně důvěryhodná.

## <a name="notes"></a>Poznámky

- V rozhraní .NET Framework 4.5 a novější verze sestavení na místní síťové sdílené složky v úplném vztahu důvěryhodnosti ve výchozím nastavení spouští; Nemáte povolení `<loadFromRemoteSources>` elementu.

- Pokud aplikace byl zkopírován z webu, je označena příznakem Windows jako webovou aplikaci, i v případě, že se nachází v místním počítači. Tento výběr můžete změnit změnou vlastnosti souboru, nebo můžete použít `<loadFromRemoteSources>` element udělte sestavení úplné důvěryhodnosti. Jako alternativu můžete použít <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> metoda načíst místní sestavení, který operační systém označil jako byla načtena z webu.

- Může se zobrazit <xref:System.IO.FileLoadException> v aplikaci, na kterém běží v aplikaci Windows Virtual PC. K tomu může dojít při pokusu o načtení souboru z propojené složky na hostitelském počítači. Může dojít také při pokusu o načtení souboru ze složky propojené přes [služby Vzdálená plocha](https://go.microsoft.com/fwlink/?LinkId=182775) (Terminálové služby). Abyste zabránili výjimku, nastavte `enabled` k `true`.

## <a name="configuration-file"></a>Konfigurační soubor

Tento prvek je obvykle používaných v konfiguračním souboru aplikace, ale je možné v další konfigurační soubory v závislosti na kontextu. Další informace najdete v článku [další implicitní používá certifikační Autority zásad: loadFromRemoteSources](https://go.microsoft.com/fwlink/p/?LinkId=266839) v blogu .NET Security.  

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak udělit úplný vztah důvěryhodnosti k sestavení načtená ze vzdáleného zdroje.

```xml
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```

## <a name="see-also"></a>Viz také:

[Více implicitní používá zásady CAS: loadFromRemoteSources](https://go.microsoft.com/fwlink/p/?LinkId=266839)  
[Postupy: spuštění částečně důvěryhodného kódu v izolovaném prostoru](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)  
[Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
[Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)  
<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>  
