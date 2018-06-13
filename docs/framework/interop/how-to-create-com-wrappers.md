---
title: 'Postupy: Vytváření obálek COM'
ms.date: 03/30/2017
helpviewer_keywords:
- COM,wrappers creating
- COM,wrappers Visual Studio
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4deb355a7b523437ae31a1d2b9c79e3b8d4f40a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33391222"
---
# <a name="how-to-create-com-wrappers"></a>Postupy: Vytváření obálek COM
Obálky modelu COM (Component Object) můžete vytvořit pomocí [!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)] funkce nebo rozhraní .NET Framework nástroje Tlbimp.exe a Regasm.exe. Obě metody generovat dva typy COM – obálky:  
  
-   A [obálka volatelná za běhu](../../../docs/framework/interop/runtime-callable-wrapper.md) z knihovny typů ke spuštění objektu COM ve spravovaném kódu.  
  
-   A [obálka volatelná aplikacemi COM](../../../docs/framework/interop/com-callable-wrapper.md) s se požadovaná nastavení registru pro spuštění spravovaného objektu v nativní aplikaci.  
  
 V [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], obálky COM můžete přidat jako odkaz na projekt.  
  
## <a name="wrapping-com-objects-in-a-managed-application"></a>Zabalení COM – objekty ve spravované aplikaci  
  
#### <a name="to-create-a-runtime-callable-wrapper-using-visual-studio"></a>Chcete-li vytvořit obálka volatelná za běhu pomocí sady Visual Studio  
  
1.  Otevřete projekt pro spravované aplikace.  
  
2.  Na **projektu** nabídky, klikněte na tlačítko **zobrazit všechny soubory**.  
  
3.  Na **projektu** nabídky, klikněte na tlačítko **přidat odkaz na**.  
  
4.  V dialogovém okně Přidat odkaz klepněte **COM** , vyberte součást, kterou chcete použít a klikněte na **OK**.  
  
     V **Průzkumníku**, Všimněte si, že komponenty modelu COM přidán do složky odkazů v projektu.  
  
 Teď můžete napsat kód pro přístup k objektu COM. Můžete začít tím, že deklarujete objekt, například s `Imports` příkaz pro [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] nebo `Using` příkaz pro [!INCLUDE[csprcslong](../../../includes/csprcslong-md.md)].  
  
> [!NOTE]
>  Pokud chcete program komponenty aplikace Microsoft Office, nejprve nainstalujte [primární zprostředkovatel komunikace s objekty sestavení sady Microsoft Office](http://go.microsoft.com/fwlink/?LinkId=50479) (PIA) z webu Microsoft Download Center. V kroku 4, vyberte nejnovější verzi k dispozici pro produkt Office, jako například chcete objektu knihovny **Microsoft Word 11.0 objektu knihovny**.  
  
#### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a>Chcete-li vytvořit obálka volatelná za běhu pomocí rozhraní .NET Framework – nástroje  
  
-   Spustit [Tlbimp.exe (Importér knihovny)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) nástroj.  
  
 Tento nástroj vytvoří sestavení obsahující metadat v době běhu pro typy definované v původní knihovny typů.  
  
## <a name="wrapping-managed-objects-in-a-native-application"></a>Zabalení spravované objekty v nativní aplikace  
  
#### <a name="to-create-a-com-callable-wrapper-using-visual-studio"></a>Chcete-li vytvořit obálka volatelná aplikacemi COM pomocí sady Visual Studio  
  
1.  Vytvoření projektu knihovny tříd pro spravované třídy, kterou chcete spustit v nativním kódu. Třída musí mít výchozí konstruktor.  
  
     Ověřte, zda máte pro vaše sestavení v souboru AssemblyInfo číslo dokončení sestávající ze čtyř částí verze. Toto číslo je požadované pro údržbu správy verzí v registru systému Windows. Další informace o čísla verzí, naleznete v části [Správa verzí sestavení](../../../docs/framework/app-domains/assembly-versioning.md).  
  
2.  Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
3.  Klikněte **zkompilovat** kartě.  
  
4.  Vyberte **zaregistrovat zprostředkovatel komunikace s objekty COM** zaškrtávací políčko.  
  
 Při sestavování projektu pro zprostředkovatele komunikace s objekty COM se automaticky registruje sestavení. Pokud vytváříte nativní aplikace [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], sestavení můžete použít klepnutím **přidat odkaz na** na **projektu** nabídky.  
  
#### <a name="to-create-a-com-callable-wrapper-using-net-framework-tools"></a>Chcete-li vytvořit obálka volatelná aplikacemi COM pomocí rozhraní .NET Framework – nástroje  
  
-   Spustit [Regasm.exe (Nástroj registrace sestavení)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) nástroj.  
  
 Tento nástroj načte metadata sestavení a přidá nezbytné položky registru. Klienti COM v důsledku toho můžete vytvořit třídy rozhraní .NET Framework transparentně. Sestavení můžete použít, jakoby byly nativní třídy COM.  
  
 Můžete spustit Regasm.exe na sestavení se nenachází v libovolného adresáře a poté spusťte [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) ho přesunout do globální mezipaměti sestavení. Přesunutí sestavení zneplatnění umístění položky registru, protože je vždy zkontrolován Pokud sestavení nebyl nalezen jinde v globální mezipaměti sestavení.  
  
## <a name="see-also"></a>Viz také  
 [Obálka volatelná za běhu](../../../docs/framework/interop/runtime-callable-wrapper.md)  
 [Obálka volatelná aplikacemi COM](../../../docs/framework/interop/com-callable-wrapper.md)
