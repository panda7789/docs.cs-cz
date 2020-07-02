---
title: 'Postupy: Vytváření obálek COM'
description: Vytváření obálek modelu COM (Component Object Model) pomocí sady Visual Studio nebo nástrojů .NET (Tlbimp.exe a Regasm.exe). Obě metody generují dva typy obálky COM.
ms.date: 03/30/2017
helpviewer_keywords:
- COM,wrappers creating
- COM,wrappers Visual Studio
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
ms.openlocfilehash: 286526c710287e6efa3e49a7f7c55e3687076e29
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617389"
---
# <a name="how-to-create-com-wrappers"></a>Postupy: Vytváření obálek COM

Obálky modelu COM (Component Object Model) můžete vytvořit pomocí funkcí sady Visual Studio 2005 nebo nástrojů .NET Framework Tlbimp.exe a Regasm.exe. Obě metody generují dva typy wrapperů COM:

- [Běhová obálka](../../standard/native-interop/runtime-callable-wrapper.md) , která se má volat z knihovny typů pro spuštění objektu COM ve spravovaném kódu.

- Obálka s možnostmi [modelu COM](../../standard/native-interop/com-callable-wrapper.md) s požadovaným nastavením registru pro spuštění spravovaného objektu v nativní aplikaci.

V aplikaci Visual Studio 2005 můžete přidat obálku COM jako odkaz na projekt.

## <a name="wrap-com-objects-in-a-managed-application"></a>Zabalení objektů COM ve spravované aplikaci

### <a name="to-create-a-runtime-callable-wrapper-using-visual-studio"></a>Vytvoření obálky s požadovanou metodou spuštění pomocí sady Visual Studio

1. Otevřete projekt pro spravovanou aplikaci.

2. V nabídce **projekt** klikněte na příkaz **Zobrazit všechny soubory**.

3. V nabídce **projekt** klikněte na příkaz **Přidat odkaz**.

4. V dialogovém okně Přidat odkaz klikněte na kartu **com** , vyberte komponentu, kterou chcete použít, a klikněte na tlačítko **OK**.

     V **Průzkumník řešení**si všimněte, že komponenta modelu COM je přidána do složky odkazy v projektu.

Nyní můžete napsat kód pro přístup k objektu COM. Můžete začít deklarováním objektu, například pomocí `Imports` příkazu pro Visual Basic nebo `Using` příkazu pro jazyk C#.

> [!NOTE]
> Pokud chcete programovat systém Microsoft Office komponenty, nejprve nainstalujte [systém Microsoft Office primární spolupracující sestavení](https://www.microsoft.com/Download/details.aspx?id=3508).
  
### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a>Vytvoření obálky s požadovanou metodou spuštění pomocí .NET Frameworkch nástrojů  
  
- Spusťte nástroj [Tlbimp.exe (importér knihovny typů)](../tools/tlbimp-exe-type-library-importer.md) .  
  
 Tento nástroj vytvoří sestavení, které obsahuje metadata modulu runtime pro typy definované v původní knihovně typů.  
  
## <a name="wrap-managed-objects-in-a-native-application"></a>Zabalení spravovaných objektů v nativní aplikaci  
  
### <a name="to-create-a-com-callable-wrapper-using-visual-studio"></a>Vytvoření obálky s požadovanou metodou COM pomocí sady Visual Studio  
  
1. Vytvořte projekt knihovny tříd pro spravovanou třídu, kterou chcete spustit v nativním kódu. Třída musí mít konstruktor bez parametrů.  
  
     Ověřte, zda máte pro sestavení v souboru AssemblyInfo celé číslo verze se čtyřmi částmi. Toto číslo je vyžadováno pro údržbu správy verzí v registru systému Windows. Další informace o číslech verzí najdete v tématu [Správa verzí sestavení](../../standard/assembly/versioning.md).  
  
2. V nabídce **projekt** klikněte na příkaz **vlastnosti**.  
  
3. Klikněte na kartu **kompilovat** .  
  
4. Zaškrtněte políčko **zaregistrovat pro zprostředkovatele komunikace s objekty COM** .  
  
 Při sestavování projektu je sestavení automaticky registrováno pro zprostředkovatele komunikace s objekty COM. Pokud vytváříte nativní aplikaci v aplikaci Visual Studio 2005, můžete použít sestavení kliknutím na **Přidat odkaz** v nabídce **projekt** .  
  
### <a name="to-create-a-com-callable-wrapper-using-net-framework-tools"></a>Vytvoření obálky s požadovanou metodou COM pomocí .NET Frameworkch nástrojů  
  
Spusťte nástroj [Regasm.exe (Nástroj pro registraci sestavení)](../tools/regasm-exe-assembly-registration-tool.md) .  
  
Tento nástroj přečte metadata sestavení a přidá nezbytné položky do registru. V důsledku toho mohou klienti modelu COM vytvářet .NET Framework třídy transparentně. Můžete použít sestavení, jako by šlo o nativní třídu COM.  
  
Můžete spustit Regasm.exe pro sestavení nacházející se v jakémkoli adresáři a potom spuštěním [Gacutil.exe (nástroj Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) ho přesunout do globální mezipaměti sestavení (GAC). Přesunutí sestavení neověřuje položky registru umístění, protože globální mezipaměť sestavení (GAC) je vždy zkoumána v případě, že sestavení není nalezeno jinde.  
  
## <a name="see-also"></a>Viz také:

- [Obálka volatelná za běhu](../../standard/native-interop/runtime-callable-wrapper.md)
- [Obálka volatelná aplikacemi COM](../../standard/native-interop/com-callable-wrapper.md)
