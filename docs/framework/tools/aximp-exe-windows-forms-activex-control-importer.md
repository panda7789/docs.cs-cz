---
title: Aximp.exe (importér ovládacích prvků ActiveX Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- ActiveX controls, hosting in Windows Forms
- ActiveX Control Importer
- type definitions, converting
- Aximp.exe
- Windows Forms ActiveX Control Importer
ms.assetid: 482c0d83-7144-4497-b626-87d2351b78d0
ms.openlocfilehash: 6d58d1df81780c3033eab7c1ac3e860adeb374b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180429"
---
# <a name="aximpexe-windows-forms-activex-control-importer"></a>Aximp.exe (importér ovládacích prvků ActiveX Windows Forms)
Importér ovládacích prvků ActiveX převede definice typů v knihovně typů modelu COM pro ovládací prvek ActiveX na ovládací prvek Windows Forms.  
  
 Windows Forms může hostovat pouze ovládací prvky windows <xref:System.Windows.Forms.Control>forms – to znamená třídy, které jsou odvozeny z . Aximp.exe generuje obálkovou třídu pro ovládací prvek ActiveX, který může být hostován na Windows Forms. To umožňuje použít stejnou podporu návrhu a programovací metody jako pro ostatní ovládací prvky Windows Forms.  
  
 Chcete-li hostovat ovládací prvek ActiveX, je nutné <xref:System.Windows.Forms.AxHost>vygenerovat ovládací prvek obálky, který je odvozen od aplikace . Tento ovládací prvek obálky obsahuje instanci původního ovládacího prvku ActiveX. Dokáže komunikovat s ovládacím prvkem ActiveX, ale je zobrazen jako ovládací prvek Windows Forms. Tento vygenerovaný ovládací prvek hostuje ovládací prvek ActiveX a zpřístupňuje jeho vlastnosti, metody a události, jako by náležely vygenerovanému ovládacímu prvku.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li nástroj spustit, použijte příkazový řádek pro vývojáře pro sadu Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace naleznete v [příkazových koncích](developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
aximp [options]{file.dll | file.ocx}  
```  
  
## <a name="remarks"></a>Poznámky  
  
|Argument|Popis|  
|--------------|-----------------|  
|*Soubor*|Název zdrojového souboru obsahujícího ovládací prvek ActiveX, který má být převeden. Argument souboru musí mít příponu .dll nebo .ocx.|  
  
|Možnost|Popis|  
|------------|-----------------|  
|`/delaysign`|Určuje, že Aximp.exe podepíše výsledný ovládací prvek pomocí zpožděného podepisování. Tuto možnost je nutné `/keycontainer:`zadat `/keyfile:`pomocí `/publickey:` možnosti , nebo option. Další informace o procesu zpožděného podepisování naleznete v [tématu Delay Signing a Assembly](../../standard/assembly/delay-sign.md).|  
|`/help`|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|`/keycontainer:`*containerName*|Podepisuje výsledný ovládací prvek silným názvem pomocí dvojice veřejného a soukromého klíče nalezené v kontejneru klíčů určeném *containerName*.|  
|`/keyfile:`*název souboru*|Výsledné řízení podení silným názvem podením pomocí oficiálního páru veřejného a soukromého klíče vydavatele, který se nachází v *názvu souboru*.|  
|`/nologo`|Potlačí zobrazení úvodního nápisu společnosti Microsoft.|  
|`/out:`*název souboru*|Určuje název sestavení, které se má vytvořit.|  
|`/publickey:`*název souboru*|Výsledný ovládací prvek podení silným názvem podení podení pomocí veřejného klíče nalezeného v souboru určeném *názvem souboru*.|  
|`/rcw:`*název souboru*|Používá určenou obálku volatelnou modulem runtime namísto generování nové. Můžete zadat více instancí. Aktuální adresář se používá pro relativní cesty. Další informace naleznete v tématu [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md).|  
|`/silent`|Potlačí zobrazování zpráv o úspěšném dokončení.|  
|`/source`|Generuje zdrojový kód jazyka C# pro obálku Windows Forms.|  
|`/verbose`|Určuje režim podrobného vypisování; zobrazuje dodatečné informace o průběhu.|  
|`/?`|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
 Aximp.exe najednou převede celé knihovny typů ovládacího prvku ActiveX a vytvoří sadu sestavení, která obsahují metadata Common Language Runtime (CML) a implementaci ovládacích prvků pro typy definované v původní knihovně typů. Generované soubory jsou pojmenovány podle následujícího vzoru:  
  
 renomovaný jazykový runtime proxy pro typy COM: *progid*.dll  
  
 Proxy systému Windows Forms pro ovládací prvky ActiveX (kde Ax označuje ActiveX): Ax*progid*.dll  
  
> [!NOTE]
> Pokud název členu ovládacího prvku ActiveX odpovídá názvu definovanému v rozhraní .NET Framework, Aximp.exe při vytváření odvozené třídy AxHost před název člena přidá „Ctl“. Například, pokud ovládací prvek ActiveX má člen nazvaný „Layout“, přejmenuje se v odvozené třídě AxHost na „CtlLayout“, protože událost Layout je definována v rámci .NET Framework.  
  
 Tyto generované soubory můžete prozkoumat pomocí nástrojů, jako je [Ildasm.exe (IL Disassembler).](ildasm-exe-il-disassembler.md)  
  
 Použití Aximp.exe za účelem generování sestavení .NET pro ovládací prvek ActiveX pro webový prohlížeč (shdocvw.dll) není podporováno.  
  
 Při spuštění Aximp.exe přes shdocvw.dll se vždy vytvoří další soubor s názvem shdocvw.dll v adresáři, ze kterého je nástroj spuštěn. Pokud je tento vygenerovaný soubor umístěn v adresáři Documents and Settings, způsobuje problémy v aplikacích Microsoft Internet Explorer a Průzkumník Windows. Po restartování počítače systém Windows hledá v adresáři Documents and Settings před adresářem system32, aby našel kopii souboru shdocvw.dll. Použije kopii, kterou najde v adresáři Documents and Settings a pokusí se načíst spravované obálky. Aplikace Internet Explorer a Průzkumník Windows nebudou správně fungovat, protože spoléhají na vykreslovací modul ve verzi shdocvw.dll v adresáři system32. Pokud nastane tento problém, odstraňte kopii souboru shdocvw.dll v adresáři Documents and Settings a restartujte počítač.  
  
 Použití Aximp.exe se souborem shdocvw.dll k vytvoření sestavení .NET pro použití při vývoji aplikace může také způsobit problémy. V tomto případě aplikace načte systémovou verzi souboru shdocvw.dll i vygenerovanou verzi a může dát přednost verzi systému. V takovém případě se při pokusu o načtení webové stránky uvnitř ovládacího prvku ActiveX webového prohlížeče uživatelům může zobrazit dialogové okno Otevřít/Uložit. Po klepnutí na tlačítko **Otevřít**bude webová stránka otevřena v aplikaci Internet Explorer. K této situaci dochází pouze u počítačů používajících aplikaci Internet Explorer verze 6 nebo starší. Chcete-li tomuto problému <xref:System.Windows.Forms.WebBrowser> zabránit, použijte spravovaný ovládací prvek nebo použijte Visual Studio ke generování spravované shdocvw.dll, jak je popsáno v [postupem: Přidat odkazy na knihovny typů](../interop/how-to-add-references-to-type-libraries.md).  
  
## <a name="example"></a>Příklad  
 Následující příkaz generuje servery MediaPlayer.dll a AxMediaPlayer.dll pro ovládací prvek `msdxm.ocx`Media Player .  
  
```console
aximp c:\systemroot\system32\msdxm.ocx  
```  
  
## <a name="see-also"></a>Viz také

- [Nástroje](index.md)
- [Ildasm.exe (IL Disassembler)](ildasm-exe-il-disassembler.md)
