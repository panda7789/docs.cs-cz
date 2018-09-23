---
title: Regasm.exe (nástroj registrace sestavení)
ms.date: 03/30/2017
helpviewer_keywords:
- Assembly Registration tool
- assemblies [.NET Framework], registering
- Regasm.exe
- registering assemblies
ms.assetid: e190e342-36ef-4651-a0b4-0e8c2c0281cb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 30b13c75907ad0bc4d6dbce6a3ecd07f1fbede11
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46586257"
---
# <a name="regasmexe-assembly-registration-tool"></a>Regasm.exe (nástroj registrace sestavení)

Nástroj Assembly Registration načte metadata v rámci sestavení a přidá nezbytné položky registru, které umožní klientům modelu COM transparentní vytvoření tříd rozhraní .NET Framework. Jakmile je třída zaregistrována, může ji libovolný klient COM použít jako třídu COM. Třída je registrována pouze jednou, při instalaci sestavení. Instance tříd z modelu COM v rámci sestavení nelze vytvořit, dokud nedojde k jejich registraci.

Ke spuštění nástroje, použijte příkazový řádek pro vývojáře pro sadu Visual Studio. Další informace najdete v tématu [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md).

V příkazovém řádku zadejte následující:

## <a name="syntax"></a>Syntaxe

```
regasm assemblyFile [options]
```

#### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*AssemblyFile*|Sestavení, která mají být registrována pomocí modelu COM.|

|Možnost|Popis|
|------------|-----------------|
|**/ codebase**|Vytvoří položku základu kódu v registru. Položka základu kódu určuje cestu k souboru sestavení, které není nainstalováno v globální mezipaměti sestavení (GAC). Tuto možnost byste neměli zadávat, pokud následně instalujete sestavení, které budete registrovat do globální mezipaměti sestavení (GAC). *AssemblyFile* argument, který zadáte **/ codebase** možnost musí být [sestavení se silným názvem](../../../docs/framework/app-domains/strong-named-assemblies.md).|
|**/ registrované**|Určuje, že tento nástroj bude odkazovat pouze na knihovny typů, které již byly zaregistrovány.|
|**/asmpath:Directory**|Určuje adresář obsahující odkazy na sestavení. Je nutné použít s **/RegFile** možnost.|
|**/nologo**|Potlačí zobrazení úvodního nápisu společnosti Microsoft.|
|**/ RegFile** [**:** *regFile*]|Generuje soubor .reg určený pro sestavení, která obsahují potřebné položky registru. Použití této možnosti nezmění registr. Tuto možnost s nelze použít **/u** nebo **/TLB** možnosti.|
|**/ silent** nebo **/s**|Potlačí zobrazování zpráv o úspěšném dokončení.|
|**/ TLB** [**:** *typeLibFile*]|Ze zadaného sestavení vytvoří knihovnu typů obsahující definice dostupných typů definovaných v rámci sestavení.|
|**/ unregister** nebo **/u**|Zruší registraci vytvořitelné třídy v *assemblyFile*. Vynechání této možnosti způsobí, že nástroj Regasm.exe zaregistruje vytvořitelné třídy v rámci sestavení.|
|**/verbose**|Určuje režim podrobného vypisování; Zobrazí seznam veškerých odkazovaných sestavení, pro které knihovnu typů musí být vytvořen, pokud zadaný **/TLB** možnost.|
|**/?** nebo   **/help**|Zobrazí syntaxi příkazu a možnosti nástroje.|

> [!NOTE]
> Možnosti příkazového řádku nástroje Regasm.exe nerozlišují malá a velká písmena. Pro jednoznačnou identifikaci je potřeba zadat dostatek parametrů. Například **/n** je ekvivalentní **/nologo** a **t:** *outfile.tlb* je ekvivalentní **/tlb:**  *OutFile.tlb*.

## <a name="remarks"></a>Poznámky

Můžete použít **/RegFile** možnost k vytvoření souboru .reg obsahujícího položky registru namísto změn přímo do registru. Registr lze na počítači aktualizovat importováním souboru .reg pomocí nástroje Editor registru (Regedit.exe). Soubor .reg neobsahuje žádné aktualizace registru, které lze provést pomocí funkcí registru definovaných uživatelem.  Všimněte si, **/RegFile** možnost generuje pouze položky registru pro spravované třídy.  Tato možnost negeneruje položky pro `TypeLibID`s nebo `InterfaceID`s.

Pokud zadáte **/TLB** možnost Regasm.exe vygeneruje a zaregistruje knihovnu typů popisující typy nalezené v sestavení. Nástroj Regasm.exe umístí vytvořenou knihovnu typů do aktuálního pracovního adresáře nebo do adresáře určeného pro výstupní soubor. Vytváření knihovny typů pro sestavení, které odkazuje na jiné sestavení, může způsobit vytvoření několika knihoven typů najednou. Knihovny typů můžete použít k poskytnutí informací o typech vývojovým nástrojům jako například Visual Studio. Neměli byste používat **/TLB** možnost sestavení při registraci se vytvořil parametrem Type Library Importer ([Tlbimp.exe](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)). Knihovnu typů nelze exportovat ze sestavení, které bylo importováno z knihovny typů. Použití **/TLB** možnost má stejný účinek jako použití Exportér knihovny typů ([Tlbexp.exe](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)) a Regasm.exe, s tím rozdílem, že Tlbexp.exe nezaregistruje knihovnu typů, vyvolá.  Pokud používáte **/TLB** možnost zaregistrovat knihovnu typů, můžete použít **/TLB** spolu s možností **/ unregister** pro zrušení registrace knihovny typů. Použitím obou možností společně dojde ke zrušení registrace knihovny typů a položek rozhraní, čímž lze značně pročistit registr.

Při registraci sestavení pro použití modelem COM nástroj Regasm.exe přidá položky do registru místního počítače. Přesněji řečeno vytvoří klíče registru závislé na verzi, které dovolují v počítači paralelně spustit více verzí stejného sestavení. Při první registraci sestavení je pro sestavení vytvořen jeden klíč na nejvyšší úrovni a je vytvořen jedinečný podklíč pro konkrétní verzi. Při každé registraci nové verze sestavení nástroj Regasm.exe vytvoří podklíč pro novou verzi.

Jako příklad lze uvést registraci spravované komponenty, myComp.dll, verze 1.0.0.0 pro použití modelem COM. Později zaregistrujete myComp.dll verze 2.0.0.0. Je možné určit, že všechny klientské aplikace modelu COM v počítači používají myComp.dll verze 2.0.0.0 a rozhodnout o zrušení registrace myComponent.dll verze 1.0.0.0. Toto schéma registru umožňuje zrušit registraci myComp.dll verze 1.0.0.0, protože je odebrán pouze podklíč verze 1.0.0.0.

Po registraci sestavení pomocí Regasm.exe, můžete nainstalovat ho [globální mezipaměti sestavení](../../../docs/framework/app-domains/gac.md) tak, aby mohlo být aktivováno z libovolného klientu com. Pokud bude sestavení aktivováno jednou aplikací, je možné je umístit do adresáře dané aplikace.

## <a name="examples"></a>Příklady

Následující příkaz zaregistruje všechny veřejné třídy obsažené v `myTest.dll`.

```
regasm myTest.dll
```

Následující příkaz vytvoří soubor `myTest.reg`, která obsahuje všechny nezbytné položky registru. Tento příkaz neprovede aktualizaci registru.

```
regasm myTest.dll /regfile:myTest.reg
```

Následující příkaz zaregistruje všechny veřejné třídy obsažené v `myTest.dll`, vygeneruje a zaregistruje knihovnu typů `myTest.tlb`, která obsahuje definice veřejných typů definovaných v `myTest.dll`.

```
regasm myTest.dll /tlb:myTest.tlb
```

## <a name="see-also"></a>Viz také:

- [Nástroje](../../../docs/framework/tools/index.md)
- [Tlbexp.exe (exportér knihovny typů)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)
- [Tlbimp.exe (importér knihovny typů)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)
- [Registrování sestav pomocí modelu COM](../../../docs/framework/interop/registering-assemblies-with-com.md)
- [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
