---
title: Regasm.exe (nástroj registrace sestavení)
description: Použijte Regasm.exe Nástroj pro registraci sestavení. Čtení metadat sestavení a přidání potřebných položek do registru, povolení klientům modelu COM, aby vytvářeli třídy .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- Assembly Registration tool
- assemblies [.NET Framework], registering
- Regasm.exe
- registering assemblies
ms.assetid: e190e342-36ef-4651-a0b4-0e8c2c0281cb
ms.openlocfilehash: a3af6a0fbc7c9c695e18448da285977f04fd72ef
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517253"
---
# <a name="regasmexe-assembly-registration-tool"></a>Regasm.exe (nástroj registrace sestavení)

Nástroj Assembly Registration načte metadata v rámci sestavení a přidá nezbytné položky registru, které umožní klientům modelu COM transparentní vytvoření tříd rozhraní .NET Framework. Jakmile je třída zaregistrována, může ji libovolný klient COM použít jako třídu COM. Třída je registrována pouze jednou, při instalaci sestavení. Instance tříd z modelu COM v rámci sestavení nelze vytvořit, dokud nedojde k jejich registraci.

Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio. Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).

V příkazovém řádku zadejte následující:

## <a name="syntax"></a>Syntaxe

```console
regasm assemblyFile [options]
```

## <a name="parameters"></a>Parametry

|Parametr|Description|
|---------------|-----------------|
|*assemblyFile*|Sestavení, která mají být registrována pomocí modelu COM.|

|Možnost|Popis|
|------------|-----------------|
|**/codebase**|Vytvoří položku základu kódu v registru. Položka základu kódu určuje cestu k souboru pro sestavení, které není nainstalováno v globální mezipaměti sestavení (GAC). Tuto možnost nezadávejte, pokud budete následně instalovat sestavení, které zaregistrujete do globální mezipaměti sestavení (GAC). Argument *assemblyFile* , který zadáte pomocí možnosti **/codebase** , musí být [sestavení se silným názvem](../../standard/assembly/strong-named.md).|
|**/registered odkazuje**|Určuje, že tento nástroj bude odkazovat pouze na knihovny typů, které již byly zaregistrovány.|
|**/asmPath: adresář**|Určuje adresář obsahující odkazy na sestavení. Musí být použit s možností **/regfile** .|
|**/nologo**|Potlačí zobrazení úvodního nápisu společnosti Microsoft.|
|**/regfile** [**:** *regfile*]|Generuje soubor .reg určený pro sestavení, která obsahují potřebné položky registru. Použití této možnosti nezmění registr. Tuto možnost nelze použít s možnostmi **/u** nebo **/TLB** .|
|**/Silent** nebo **/s**|Potlačí zobrazování zpráv o úspěšném dokončení.|
|**/TLB** [**:** *typeLibFile*]|Ze zadaného sestavení vytvoří knihovnu typů obsahující definice dostupných typů definovaných v rámci sestavení.|
|**/Unregister** nebo **/u**|Zruší registraci tříd, které se v *assemblyFile*nacházejí. Vynechání této možnosti způsobí, že nástroj Regasm.exe zaregistruje vytvořitelné třídy v rámci sestavení.|
|**/verbose**|Určuje režim podrobného výpisu; Zobrazí seznam všech odkazovaných sestavení, pro které je třeba generovat knihovnu typů, pokud je zadána pomocí možnosti **/TLB** .|
|**/?** nebo **/help**|Zobrazí syntaxi příkazu a možnosti nástroje.|

> [!NOTE]
> Možnosti příkazového řádku nástroje Regasm.exe nerozlišují malá a velká písmena. Pro jednoznačnou identifikaci je potřeba zadat dostatek parametrů. Například **/n** je ekvivalentem **/nologo** a **/t:** *soubor. tlb* je ekvivalentní k **/TLB:** *soubor. tlb*.

## <a name="remarks"></a>Poznámky

K vygenerování souboru. reg, který obsahuje položky registru, místo provedení změn přímo v registru můžete použít možnost **/regfile** . Registr lze na počítači aktualizovat importováním souboru .reg pomocí nástroje Editor registru (Regedit.exe). Soubor. reg neobsahuje žádné aktualizace registru, které by mohly být provedeny uživatelsky definovanými funkcemi registru. Možnost **/regfile** vygeneruje pouze položky registru pro spravované třídy. Tato možnost negeneruje položky pro `TypeLibID` s nebo `InterfaceID` s.

Když zadáte možnost **/TLB** , Regasm.exe generuje a zaregistruje knihovnu typů popisující typy nalezené v sestavení. Nástroj Regasm.exe umístí vytvořenou knihovnu typů do aktuálního pracovního adresáře nebo do adresáře určeného pro výstupní soubor. Vytváření knihovny typů pro sestavení, které odkazuje na jiné sestavení, může způsobit vytvoření několika knihoven typů najednou. Knihovnu typů můžete použít k poskytnutí informací o typech vývojářským nástrojům, jako je Visual Studio. Nepoužívejte možnost **/TLB** , pokud sestavení, které zaregistrujete, vytvořil Nástroj pro import knihovny typů ([Tlbimp.exe](tlbimp-exe-type-library-importer.md)). Knihovnu typů nelze exportovat ze sestavení, které bylo importováno z knihovny typů. Použití možnosti **/TLB** má stejný účinek jako použití exportéru knihovny typů ([Tlbexp.exe](tlbexp-exe-type-library-exporter.md)) a Regasm.exe, s výjimkou, že Tlbexp.exe neregistruje knihovnu typů, kterou vytváří.  Použijete-li možnost **/TLB** k registraci knihovny typů, můžete použít možnost **/TLB** s možností **/Unregister** pro zrušení registrace knihovny typů. Použitím obou možností společně dojde ke zrušení registrace knihovny typů a položek rozhraní, čímž lze značně pročistit registr.

Při registraci sestavení pro použití modelem COM nástroj Regasm.exe přidá položky do registru místního počítače. Přesněji řečeno vytvoří klíče registru závislé na verzi, které dovolují v počítači paralelně spustit více verzí stejného sestavení. Při prvním zaregistrování sestavení se vytvoří jeden klíč nejvyšší úrovně pro sestavení a pro konkrétní verzi se vytvoří jedinečný podklíč. Při každé registraci nové verze sestavení nástroj Regasm.exe vytvoří podklíč pro novou verzi.

Jako příklad lze uvést registraci spravované komponenty, myComp.dll, verze 1.0.0.0 pro použití modelem COM. Později zaregistrujete myComp.dll verze 2.0.0.0. Je možné určit, že všechny klientské aplikace modelu COM v počítači používají myComp.dll verze 2.0.0.0 a rozhodnout o zrušení registrace myComponent.dll verze 1.0.0.0. Toto schéma registru umožňuje zrušit registraci myComp.dll verze 1.0.0.0, protože je odebrán pouze podklíč verze 1.0.0.0.

Po registraci sestavení pomocí Regasm.exe jej můžete nainstalovat do [globální mezipaměti sestavení (GAC](../app-domains/gac.md) ), aby jej bylo možné aktivovat z libovolného klienta modelu COM. Pokud bude sestavení aktivováno jednou aplikací, je možné je umístit do adresáře dané aplikace.

## <a name="examples"></a>Příklady

Následující příkaz registruje všechny veřejné třídy obsažené v `myTest.dll` .

```console
regasm myTest.dll
```

Následující příkaz vygeneruje soubor `myTest.reg` , který obsahuje všechny nezbytné položky registru. Tento příkaz neprovede aktualizaci registru.

```console
regasm myTest.dll /regfile:myTest.reg
```

Následující příkaz registruje všechny veřejné třídy obsažené v a `myTest.dll` generuje a zaregistruje knihovnu typů `myTest.tlb` , která obsahuje definice všech veřejných typů definovaných v `myTest.dll` .

```console
regasm myTest.dll /tlb:myTest.tlb
```

## <a name="see-also"></a>Viz také

- [Nástroje](index.md)
- [Tlbexp.exe (typ Exportér knihovny)](tlbexp-exe-type-library-exporter.md)
- [Tlbimp.exe (importér knihovny typů)](tlbimp-exe-type-library-importer.md)
- [Registrování sestav pomocí modelu COM](../interop/registering-assemblies-with-com.md)
- [Výzvy příkazového řádku](developer-command-prompt-for-vs.md)
