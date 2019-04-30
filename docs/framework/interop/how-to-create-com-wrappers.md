---
title: 'Postupy: Vytváření obálek COM'
ms.date: 03/30/2017
helpviewer_keywords:
- COM,wrappers creating
- COM,wrappers Visual Studio
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c26c84ece1231a4e118144c163fa3e9c7619301
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61875742"
---
# <a name="how-to-create-com-wrappers"></a>Postupy: Vytváření obálek COM

Obálky objektu modelu COM (Component) můžete vytvořit pomocí funkce sady Visual Studio 2005 nebo rozhraní .NET Framework nástroje Tlbimp.exe a Regasm.exe. Obě metody vygenerovat dva typy COM – obálky:

- A [obálka volatelná za běhu](../../../docs/framework/interop/runtime-callable-wrapper.md) z knihovny typů pro spuštění objekt modelu COM ve spravovaném kódu.

- A [obálka volatelná aplikacemi COM](../../../docs/framework/interop/com-callable-wrapper.md) s se požadovaná nastavení registru pro spuštění spravovaného objektu v nativní aplikaci.

V sadě Visual Studio 2005 můžete přidat obálky COM jako odkaz na svůj projekt.

## <a name="wrap-com-objects-in-a-managed-application"></a>Objekty COM zabalte ve spravované aplikaci

### <a name="to-create-a-runtime-callable-wrapper-using-visual-studio"></a>Chcete-li vytvořit obálka volatelná za běhu pomocí sady Visual Studio

1. Otevřete projekt pro spravovanou aplikaci.

2. Na **projektu** nabídky, klikněte na tlačítko **zobrazit všechny soubory**.

3. Na **projektu** nabídky, klikněte na tlačítko **přidat odkaz**.

4. V dialogovém okně Přidat odkaz na tlačítko **COM** kartu, vyberte komponentu, kterou chcete použít a klikněte na tlačítko **OK**.

     V **Průzkumníka řešení**, mějte na paměti, že komponenty modelu COM je přidán do složky odkazy ve vašem projektu.

Teď můžete psát kód pro přístup k objektu COM. Můžete začít deklarováním objektu, například pomocí `Imports` příkaz pro [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] nebo `Using` příkaz pro [!INCLUDE[csprcslong](../../../includes/csprcslong-md.md)].

> [!NOTE]
> Pokud chcete program komponenty Microsoft Office, nejdřív nainstalovat [Microsoft Office Primary Interop Assemblies](https://go.microsoft.com/fwlink/?LinkId=50479) (PIA) z webu Microsoft Download Center. V kroku 4, vyberte nejnovější verzi k dispozici produktu Office, jako například chcete objekt knihovny **Microsoft Word 11.0 objekt knihovny**.  
  
### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a>Chcete-li vytvořit obálka volatelná za běhu pomocí rozhraní .NET Framework – nástroje  
  
- Spustit [Tlbimp.exe (Importér knihovny typů)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) nástroj.  
  
 Tento nástroj vytvoří sestavení, který obsahuje metadat v době běhu pro typy definované v původní knihovně typů.  
  
## <a name="wrap-managed-objects-in-a-native-application"></a>Uveďte spravované objekty v nativní aplikaci  
  
### <a name="to-create-a-com-callable-wrapper-using-visual-studio"></a>Chcete-li vytvořit obálka volatelná aplikacemi COM pomocí sady Visual Studio  
  
1. Vytvořte projekt knihovny tříd pro spravované třídy, které chcete spouštět v nativním kódu. Třída musí mít výchozí konstruktor.  
  
     Ověřte, že máte číslo úplné verze složené ze čtyř částí pro vaše sestavení v souboru AssemblyInfo. Toto číslo je vyžadován pro zachování verzí v registru Windows. Další informace o číslech verzí najdete v tématu [Správa verzí sestavení](../../../docs/framework/app-domains/assembly-versioning.md).  
  
2. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
3. Klikněte na tlačítko **kompilaci** kartu.  
  
4. Vyberte **zaregistrovat pro interoperabilitu COM** zaškrtávací políčko.  
  
 Při vytváření projektu pro zprostředkovatele komunikace s objekty COM se automaticky registruje sestavení. Pokud vytváříte nativní aplikace v sadě Visual Studio 2005, můžete kliknutím na použít sestavení **přidat odkaz** na **projektu** nabídky.  
  
### <a name="to-create-a-com-callable-wrapper-using-net-framework-tools"></a>Chcete-li vytvořit obálka volatelná aplikacemi COM pomocí rozhraní .NET Framework – nástroje  
  
Spustit [Regasm.exe (Nástroj registrace sestavení)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) nástroj.  
  
Tento nástroj načte metadata sestavení a přidá nezbytné položky registru. Klienti modelu COM v důsledku toho můžete vytvořit třídy rozhraní .NET Framework transparentně. Sestavení můžete použít, jako by šlo nativních tříd modelu COM.  
  
Můžete spustit Regasm.exe na sestavení se nenachází v žádné adresáře a spusťte [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) ji přesunout do globální mezipaměti sestavení. Přesun sestavení nedojde k zneplatnění umístění položky registru, protože globální mezipaměti sestavení je vždy zkontrolován, pokud se sestavení nenajde jinde.  
  
## <a name="see-also"></a>Viz také:

- [Obálka volatelná za běhu](../../../docs/framework/interop/runtime-callable-wrapper.md)
- [Obálka volatelná aplikacemi COM](../../../docs/framework/interop/com-callable-wrapper.md)
