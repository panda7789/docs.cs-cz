---
title: Regasm.exe (nástroj registrace sestavení)
ms.date: 03/30/2017
helpviewer_keywords:
- Assembly Registration tool
- assemblies [.NET Framework], registering
- Regasm.exe
- registering assemblies
ms.assetid: e190e342-36ef-4651-a0b4-0e8c2c0281cb
ms.openlocfilehash: 45b4c6c08d3afb948444a8c97dc32bd41f2615ce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73104953"
---
# <a name="regasmexe-assembly-registration-tool"></a>Regasm.exe (nástroj registrace sestavení)

Nástroj Assembly Registration načte metadata v rámci sestavení a přidá nezbytné položky registru, které umožní klientům modelu COM transparentní vytvoření tříd rozhraní .NET Framework. Jakmile je třída zaregistrována, může ji libovolný klient COM použít jako třídu COM. Třída je registrována pouze jednou, při instalaci sestavení. Instance tříd z modelu COM v rámci sestavení nelze vytvořit, dokud nedojde k jejich registraci.

Chcete-li nástroj spustit, použijte příkazový řádek pro vývojáře pro sadu Visual Studio. Další informace naleznete v [příkazových koncích](developer-command-prompt-for-vs.md).

V příkazovém řádku zadejte následující:

## <a name="syntax"></a>Syntaxe

```console
regasm assemblyFile [options]
```

## <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Assemblyfile*|Sestavení, která mají být registrována pomocí modelu COM.|

|Možnost|Popis|
|------------|-----------------|
|**/codebase**|Vytvoří položku základu kódu v registru. Položka základu kódu určuje cestu k souboru sestavení, které není nainstalováno v globální mezipaměti sestavení (GAC). Tuto možnost byste neměli zadávat, pokud následně instalujete sestavení, které budete registrovat do globální mezipaměti sestavení (GAC). Argument *assemblyFile,* který zadáte pomocí možnosti **/codebase,** musí být [sestavení se silným názvem](../../standard/assembly/strong-named.md).|
|**/registrováno**|Určuje, že tento nástroj bude odkazovat pouze na knihovny typů, které již byly zaregistrovány.|
|**/asmpath:adresář**|Určuje adresář obsahující odkazy na sestavení. Musí být použit s **parametrem /regfile.**|
|**/nologo**|Potlačí zobrazení úvodního nápisu společnosti Microsoft.|
|**/regfile** [**:** *regFile*]|Generuje soubor .reg určený pro sestavení, která obsahují potřebné položky registru. Použití této možnosti nezmění registr. Tuto možnost nelze použít s možnostmi **/u** nebo **/tlb.**|
|**/tichý** nebo **/s**|Potlačí zobrazování zpráv o úspěšném dokončení.|
|**/tlb** [**:** *typeLibFile*]|Ze zadaného sestavení vytvoří knihovnu typů obsahující definice dostupných typů definovaných v rámci sestavení.|
|**/unregister** nebo **/u**|Zruší registrace creatable třídy nalezené v *assemblyFile*. Vynechání této možnosti způsobí, že nástroj Regasm.exe zaregistruje vytvořitelné třídy v rámci sestavení.|
|**/podrobné informace**|Určuje podrobný režim; zobrazí seznam všech odkazovaných sestavení, pro která je třeba vygenerovat knihovnu typů, pokud je zadána s parametrem **/tlb.**|
|**/?** nebo **/help**|Zobrazí syntaxi příkazu a možnosti nástroje.|

> [!NOTE]
> Možnosti příkazového řádku nástroje Regasm.exe nerozlišují malá a velká písmena. Pro jednoznačnou identifikaci je potřeba zadat dostatek parametrů. Například **/n** je ekvivalentní **/nologo** a **/t:** *outfile.tlb* je ekvivalentní **/tlb:** *outfile.tlb*.

## <a name="remarks"></a>Poznámky

Možnost **/regfile** můžete použít ke generování souboru REG, který obsahuje položky registru namísto provádění změn přímo do registru. Registr lze na počítači aktualizovat importováním souboru .reg pomocí nástroje Editor registru (Regedit.exe). Soubor .reg neobsahuje žádné aktualizace registru, které lze provést pomocí funkcí registru definovaných uživatelem.  Všimněte si, že **možnost /regfile** vydává pouze položky registru pro spravované třídy.  Tato možnost nevyzařuje položky `TypeLibID` `InterfaceID`pro s nebo s.

Když zadáte **/tlb** možnost, Regasm.exe generuje a registruje knihovnu typů popisující typy nalezené v sestavení. Nástroj Regasm.exe umístí vytvořenou knihovnu typů do aktuálního pracovního adresáře nebo do adresáře určeného pro výstupní soubor. Vytváření knihovny typů pro sestavení, které odkazuje na jiné sestavení, může způsobit vytvoření několika knihoven typů najednou. Knihovnu typů můžete použít k poskytování informací o typu vývojovým nástrojům, jako je Visual Studio. Možnost **/tlb** byste neměli používat, pokud bylo sestavení, které registrujete, vytvořeno importem knihovny typů ([Tlbimp.exe](tlbimp-exe-type-library-importer.md)). Knihovnu typů nelze exportovat ze sestavení, které bylo importováno z knihovny typů. Použití **možnosti /tlb** má stejný účinek jako použití type library exporter ([Tlbexp.exe](tlbexp-exe-type-library-exporter.md)) a Regasm.exe s výjimkou, že tlbexp.exe neregistruje knihovnu typů, kterou vytváří.  Pokud použijete možnost **/tlb** k registraci knihovny typů, můžete použít možnost **/tlb** s parametrem **/unregister** pro zrušení registrace knihovny typů. Použitím obou možností společně dojde ke zrušení registrace knihovny typů a položek rozhraní, čímž lze značně pročistit registr.

Při registraci sestavení pro použití modelem COM nástroj Regasm.exe přidá položky do registru místního počítače. Přesněji řečeno vytvoří klíče registru závislé na verzi, které dovolují v počítači paralelně spustit více verzí stejného sestavení. Při první registraci sestavení je pro sestavení vytvořen jeden klíč na nejvyšší úrovni a je vytvořen jedinečný podklíč pro konkrétní verzi. Při každé registraci nové verze sestavení nástroj Regasm.exe vytvoří podklíč pro novou verzi.

Jako příklad lze uvést registraci spravované komponenty, myComp.dll, verze 1.0.0.0 pro použití modelem COM. Později zaregistrujete myComp.dll verze 2.0.0.0. Je možné určit, že všechny klientské aplikace modelu COM v počítači používají myComp.dll verze 2.0.0.0 a rozhodnout o zrušení registrace myComponent.dll verze 1.0.0.0. Toto schéma registru umožňuje zrušit registraci myComp.dll verze 1.0.0.0, protože je odebrán pouze podklíč verze 1.0.0.0.

Po registraci sestavení pomocí programu Regasm.exe jej můžete nainstalovat do [globální mezipaměti sestavení,](../app-domains/gac.md) aby bylo možné jej aktivovat z libovolného klienta COM. Pokud bude sestavení aktivováno jednou aplikací, je možné je umístit do adresáře dané aplikace.

## <a name="examples"></a>Příklady

Následující příkaz registruje všechny veřejné `myTest.dll`třídy obsažené v .

```console
regasm myTest.dll
```

Následující příkaz generuje soubor `myTest.reg`, který obsahuje všechny potřebné položky registru. Tento příkaz neprovede aktualizaci registru.

```console
regasm myTest.dll /regfile:myTest.reg
```

Následující příkaz registruje všechny veřejné `myTest.dll`třídy obsažené v , a `myTest.tlb`generuje a registruje knihovnu typů `myTest.dll`, která obsahuje definice všech veřejných typů definovaných v .

```console
regasm myTest.dll /tlb:myTest.tlb
```

## <a name="see-also"></a>Viz také

- [Nástroje](index.md)
- [Tlbexp.exe (exportér knihovny typů)](tlbexp-exe-type-library-exporter.md)
- [Tlbimp.exe (importér knihovny typů)](tlbimp-exe-type-library-importer.md)
- [Registrování sestav pomocí modelu COM](../interop/registering-assemblies-with-com.md)
- [Příkazové řádky](developer-command-prompt-for-vs.md)
