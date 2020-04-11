---
title: 'Postupy: Vytváření obálek COM'
ms.date: 03/30/2017
helpviewer_keywords:
- COM,wrappers creating
- COM,wrappers Visual Studio
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
ms.openlocfilehash: 035d6439ec90426d7b68e05043ea8b6722f81d28
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121603"
---
# <a name="how-to-create-com-wrappers"></a>Postupy: Vytváření obálek COM

Obálky com (Com) můžete vytvořit pomocí funkcí sady Visual Studio 2005 nebo nástrojů rozhraní Tlbimp.exe a Regasm.exe. Obě metody generují dva typy obalů com:

- [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) z knihovny typů pro spuštění objektu COM ve spravovaném kódu.

- Com [Callable Wrapper](../../standard/native-interop/com-callable-wrapper.md) s požadovaným nastavením registru pro spuštění spravovaného objektu v nativní aplikaci.

V sadě Visual Studio 2005 můžete přidat obálku COM jako odkaz na váš projekt.

## <a name="wrap-com-objects-in-a-managed-application"></a>Zalamování objektů COM ve spravované aplikaci

### <a name="to-create-a-runtime-callable-wrapper-using-visual-studio"></a>Vytvoření runtime volatelnéobálky pomocí sady Visual Studio

1. Otevřete projekt pro spravovanou aplikaci.

2. V nabídce **Project** klepněte na příkaz **Zobrazit všechny soubory**.

3. V nabídce **Project** klepněte na **tlačítko Přidat odkaz**.

4. V dialogovém okně Přidat odkaz klepněte na kartu **COM,** vyberte komponentu, kterou chcete použít, a klepněte na **tlačítko OK**.

     V **Průzkumníku řešení**si všimněte, že komponenta MODELU COM je přidána do složky Reference v projektu.

Nyní můžete napsat kód pro přístup k objektu COM. Můžete začít deklarováním objektu, `Imports` například s příkazem pro visual basic nebo příkazem `Using` pro C#.

> [!NOTE]
> Chcete-li naprogramovat součásti sady Microsoft Office, nainstalujte nejprve [redistribuovatelné sestavení primárních meziop sady Microsoft Office](https://www.microsoft.com/Download/details.aspx?id=3508).
  
### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a>Vytvoření runtime volatelnéobálky pomocí nástrojů rozhraní .NET Framework  
  
- Spusťte nástroj [Tlbimp.exe (Import type library).](../tools/tlbimp-exe-type-library-importer.md)  
  
 Tento nástroj vytvoří sestavení, které obsahuje metadata za běhu pro typy definované v původní knihovně typů.  
  
## <a name="wrap-managed-objects-in-a-native-application"></a>Zalamování spravovaných objektů v nativní aplikaci  
  
### <a name="to-create-a-com-callable-wrapper-using-visual-studio"></a>Vytvoření popisku s volatelným pomocí sady Visual Studio  
  
1. Vytvořte projekt knihovny tříd pro spravovanou třídu, kterou chcete spustit v nativním kódu. Třída musí mít konstruktor bez parametrů.  
  
     Ověřte, zda máte úplné číslo čtyřdílné verze pro sestavení v souboru AssemblyInfo. Toto číslo je vyžadováno pro údržbu správy verzí v registru systému Windows. Další informace o číslech verzí naleznete v [tématu Správa verzí sestavení](../../standard/assembly/versioning.md).  
  
2. V nabídce **Project** klepněte na **položku Vlastnosti**.  
  
3. Klikněte na kartu **Kompilace.**  
  
4. Zaškrtněte políčko **Registrovat se pro interop com.**  
  
 Při vytváření projektu je sestavení automaticky registrováno pro interop COM. Pokud vytváříte nativní aplikaci v sadě Visual Studio 2005, můžete toto sestavení použít klepnutím na tlačítko **Přidat odkaz** v nabídce **Projekt.**  
  
### <a name="to-create-a-com-callable-wrapper-using-net-framework-tools"></a>Vytvoření volatelnéobálky COM pomocí nástrojů rozhraní .NET Framework  
  
Spusťte nástroj [Regasm.exe (Nástroj pro registraci sestavy).](../tools/regasm-exe-assembly-registration-tool.md)  
  
Tento nástroj přečte metadata sestavení a přidá potřebné položky do registru. V důsledku toho mohou klienti COM vytvářet třídy rozhraní .NET Framework transparentně. Sestavení můžete použít, jako by se jednalo o nativní třídu COM.  
  
Regasm.exe můžete spustit v sestavení umístěném v libovolném adresáři a potom spustit [soubor Gacutil.exe (Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) a přesunout jej do globální mezipaměti sestavení. Přesunutím sestavení není zneplatnění položky registru umístění, protože globální mezipaměť sestavení je vždy zkontrolována, pokud není sestavení nalezeno jinde.  
  
## <a name="see-also"></a>Viz také

- [Obálka volatelná za běhu](../../standard/native-interop/runtime-callable-wrapper.md)
- [Obálka volatelná aplikacemi COM](../../standard/native-interop/com-callable-wrapper.md)
