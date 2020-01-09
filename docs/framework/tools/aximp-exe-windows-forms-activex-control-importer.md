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
ms.openlocfilehash: a1b061b480b3e22b136a6373ddb87cf9d2233457
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715787"
---
# <a name="aximpexe-windows-forms-activex-control-importer"></a>Aximp.exe (importér ovládacích prvků ActiveX Windows Forms)
Importér ovládacích prvků ActiveX převede definice typů v knihovně typů modelu COM pro ovládací prvek ActiveX na ovládací prvek Windows Forms.  
  
 Model Windows Forms mohou hostovat pouze model Windows Forms ovládací prvky – to znamená třídy, které jsou odvozeny z <xref:System.Windows.Forms.Control>. Aximp.exe generuje obálkovou třídu pro ovládací prvek ActiveX, který může být hostován na Windows Forms. To umožňuje použít stejnou podporu návrhu a programovací metody jako pro ostatní ovládací prvky Windows Forms.  
  
 Chcete-li hostovat ovládací prvek ActiveX, je nutné vygenerovat ovládací prvek obálky, který je odvozen z <xref:System.Windows.Forms.AxHost>. Tento ovládací prvek obálky obsahuje instanci původního ovládacího prvku ActiveX. Dokáže komunikovat s ovládacím prvkem ActiveX, ale je zobrazen jako ovládací prvek Windows Forms. Tento vygenerovaný ovládací prvek hostuje ovládací prvek ActiveX a zpřístupňuje jeho vlastnosti, metody a události, jako by náležely vygenerovanému ovládacímu prvku.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
aximp [options]{file.dll | file.ocx}  
```  
  
## <a name="remarks"></a>Poznámky  
  
|Argument|Popis|  
|--------------|-----------------|  
|*souborů*|Název zdrojového souboru obsahujícího ovládací prvek ActiveX, který má být převeden. Argument souboru musí mít příponu .dll nebo .ocx.|  
  
|Možnost|Popis|  
|------------|-----------------|  
|`/delaysign`|Určuje, že Aximp.exe podepíše výsledný ovládací prvek pomocí zpožděného podepisování. Tuto možnost je nutné zadat buď s možností `/keycontainer:`, `/keyfile:`nebo `/publickey:`. Další informace o procesu opožděného podepisování naleznete v tématu [Zpožděné podepisování sestavení](../../standard/assembly/delay-sign.md).|  
|`/help`|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|`/keycontainer:` *containerName*|Podepíše výsledný ovládací prvek se silným názvem pomocí dvojice veřejného a privátního klíče nalezené v kontejneru klíčů určeném parametrem *ContainerName*.|  
|`/keyfile:` *název souboru*|Podepíše výsledný ovládací prvek se silným názvem pomocí páru oficiálního veřejného/soukromého klíče vydavatele, který se nachází v *souboru filename*.|  
|`/nologo`|Potlačí zobrazení úvodního nápisu společnosti Microsoft.|  
|`/out:` *název souboru*|Určuje název sestavení, které se má vytvořit.|  
|`/publickey:` *název souboru*|Podepíše výsledný ovládací prvek se silným názvem pomocí veřejného klíče, který se nachází v souboru určeném parametrem *filename*.|  
|`/rcw:` *název souboru*|Používá určenou obálku volatelnou modulem runtime namísto generování nové. Můžete zadat více instancí. Aktuální adresář se používá pro relativní cesty. Další informace najdete v tématu [obálka s vydanou modulem runtime](../../standard/native-interop/runtime-callable-wrapper.md).|  
|`/silent`|Potlačí zobrazování zpráv o úspěšném dokončení.|  
|`/source`|Generuje zdrojový kód jazyka C# pro obálku Windows Forms.|  
|`/verbose`|Určuje režim podrobného vypisování; zobrazuje dodatečné informace o průběhu.|  
|`/?`|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
 Aximp.exe najednou převede celé knihovny typů ovládacího prvku ActiveX a vytvoří sadu sestavení, která obsahují metadata Common Language Runtime (CML) a implementaci ovládacích prvků pro typy definované v původní knihovně typů. Generované soubory jsou pojmenovány podle následujícího vzoru:  
  
 proxy pro modul CLR (Common Language Runtime) pro typy COM: *ProgID*. dll  
  
 Model Windows Forms proxy pro ovládací prvky ActiveX (kde AX označuje ActiveX): AX*ProgID*. dll  
  
> [!NOTE]
> Pokud název členu ovládacího prvku ActiveX odpovídá názvu definovanému v rozhraní .NET Framework, Aximp.exe při vytváření odvozené třídy AxHost před název člena přidá „Ctl“. Například, pokud ovládací prvek ActiveX má člen nazvaný „Layout“, přejmenuje se v odvozené třídě AxHost na „CtlLayout“, protože událost Layout je definována v rámci .NET Framework.  
  
 Tyto generované soubory můžete prozkoumávat pomocí nástrojů, jako je [Ildasm. exe (IL Disassembler)](ildasm-exe-il-disassembler.md).  
  
 Použití Aximp.exe za účelem generování sestavení .NET pro ovládací prvek ActiveX pro webový prohlížeč (shdocvw.dll) není podporováno.  
  
 Při spuštění Aximp.exe přes shdocvw.dll se vždy vytvoří další soubor s názvem shdocvw.dll v adresáři, ze kterého je nástroj spuštěn. Pokud je tento vygenerovaný soubor umístěn v adresáři Documents and Settings, způsobuje problémy v aplikacích Microsoft Internet Explorer a Průzkumník Windows. Po restartování počítače systém Windows hledá v adresáři Documents and Settings před adresářem system32, aby našel kopii souboru shdocvw.dll. Použije kopii, kterou najde v adresáři Documents and Settings a pokusí se načíst spravované obálky. Aplikace Internet Explorer a Průzkumník Windows nebudou správně fungovat, protože spoléhají na vykreslovací modul ve verzi shdocvw.dll v adresáři system32. Pokud nastane tento problém, odstraňte kopii souboru shdocvw.dll v adresáři Documents and Settings a restartujte počítač.  
  
 Použití Aximp.exe se souborem shdocvw.dll k vytvoření sestavení .NET pro použití při vývoji aplikace může také způsobit problémy. V tomto případě aplikace načte systémovou verzi souboru shdocvw.dll i vygenerovanou verzi a může dát přednost verzi systému. V takovém případě se při pokusu o načtení webové stránky uvnitř ovládacího prvku ActiveX webového prohlížeče uživatelům může zobrazit dialogové okno Otevřít/Uložit. Když uživatel klikne na tlačítko **otevřít**, Webová stránka se otevře v aplikaci Internet Explorer. K této situaci dochází pouze u počítačů používajících aplikaci Internet Explorer verze 6 nebo starší. Chcete-li předejít tomuto problému, použijte ovládací prvek Managed <xref:System.Windows.Forms.WebBrowser> nebo použijte Visual Studio k vygenerování spravované knihovny Shdocvw. dll, jak je popsáno v tématu [Postupy: Přidání odkazů do knihoven typů](../interop/how-to-add-references-to-type-libraries.md).  
  
## <a name="example"></a>Příklad  
 Následující příkaz generuje MediaPlayer. dll a AxMediaPlayer. dll pro `msdxm.ocx`ovládacího prvku Media Player.  
  
```console 
aximp c:\systemroot\system32\msdxm.ocx  
```  
  
## <a name="see-also"></a>Viz také:

- [Nástroje](index.md)
- [Ildasm.exe (IL Disassembler)](ildasm-exe-il-disassembler.md)
