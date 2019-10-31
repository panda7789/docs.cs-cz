---
title: 'Postupy: Vytváření obálek COM'
ms.date: 03/30/2017
helpviewer_keywords:
- COM,wrappers creating
- COM,wrappers Visual Studio
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
ms.openlocfilehash: 623df8aa86d25d9a57d3039bee01b0ee39d402a8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123943"
---
# <a name="how-to-create-com-wrappers"></a>Postupy: Vytváření obálek COM

Obálky modelu COM (Component Object Model) můžete vytvořit pomocí funkcí sady Visual Studio 2005 nebo nástrojů .NET Framework nástroje Tlbimp. exe a Regasm. exe. Obě metody generují dva typy wrapperů COM:

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

Nyní můžete napsat kód pro přístup k objektu COM. Můžete začít deklarováním objektu, například pomocí příkazu `Imports` pro Visual Basic nebo příkazu `Using` pro C#.

> [!NOTE]
> Pokud chcete programovat součásti systém Microsoft Office komponenty, nejprve nainstalujte [systém Microsoft Office primární spolupráce sestavení](https://go.microsoft.com/fwlink/?LinkId=50479) (PIA) z webu Microsoft Download Center. V kroku 4 vyberte nejnovější verzi knihovny objektů, kterou chcete použít pro požadovaný produkt Office, například **knihovnu objektů Microsoft Word 11,0**.  
  
### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a>Vytvoření obálky s požadovanou metodou spuštění pomocí .NET Frameworkch nástrojů  
  
- Spusťte nástroj [Tlbimp. exe (importér knihovny typů)](../tools/tlbimp-exe-type-library-importer.md) .  
  
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
  
Spusťte nástroj [Regasm. exe (Nástroj pro registraci sestavení)](../tools/regasm-exe-assembly-registration-tool.md) .  
  
Tento nástroj přečte metadata sestavení a přidá nezbytné položky do registru. V důsledku toho mohou klienti modelu COM vytvářet .NET Framework třídy transparentně. Můžete použít sestavení, jako by šlo o nativní třídu COM.  
  
Můžete spustit nástroj Regasm. exe pro sestavení nacházející se v jakémkoli adresáři a poté spustit nástroj [Gacutil. exe (nástroj Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) , aby jej bylo možné přesunout do globální mezipaměti sestavení (GAC). Přesunutí sestavení neověřuje položky registru umístění, protože globální mezipaměť sestavení (GAC) je vždy zkoumána v případě, že sestavení není nalezeno jinde.  
  
## <a name="see-also"></a>Viz také:

- [Obálka volatelná za běhu](../../standard/native-interop/runtime-callable-wrapper.md)
- [Obálka volatelná aplikacemi COM](../../standard/native-interop/com-callable-wrapper.md)
