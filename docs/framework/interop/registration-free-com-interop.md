---
title: Zprostředkovatel komunikace s objekty COM bez registrace
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], interop
- COM interop, registration-free COM interop
- registration-free COM interop
- manifests [.NET Framework]
- registration-free activation
- object activation
- registration-free COM interop, about registration-free COM interop
ms.assetid: 90f308b9-82dc-414a-bce1-77e0155e56bd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a3de327001f987b6c35d547b7cf3cbe7feeac49
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648528"
---
# <a name="registration-free-com-interop"></a>Zprostředkovatel komunikace s objekty COM bez registrace
Spolupráci s COM bez registrace se aktivuje komponenty bez použití registru Windows k ukládání informací o sestavení. Místo registrace komponenty v počítači se během nasazení, vytvářet soubory manifestu Win32 – vizuální styl v době návrhu, které obsahují informace o aktivaci a vazby. Tyto soubory manifestu, spíše než klíče registru, směrovat aktivační objekt.  
  
 Pomocí aktivace bez registrace pro vaše sestavení místo registrace během nasazení nabízí dvě výhody:  
  
- Můžete určit, kterou verzi knihovny DLL je aktivován, když je více než jedna verze nainstalovány v počítači.  
  
- Koncoví uživatelé mohou používat příkazu XCOPY nebo FTP kopírovat aplikaci do příslušného adresáře v počítači. Aplikace se dá spustit pak z tohoto adresáře.  
  
 Tato část popisuje dva typy manifesty potřeba pro spolupráci s COM bez registrace: manifesty aplikace a komponenty. Tyto manifestů jsou soubory formátu XML. Manifest aplikace, který je vytvořen vývojář aplikací, obsahuje metadata popisující sestavení a závislosti sestavení. Manifest součásti vytvořený vývojářem komponenty obsahuje informace, jinak se nachází v registru Windows.  
  
### <a name="requirements-for-registration-free-com-interop"></a>Požadavky pro spolupráci s COM bez registrace  
  
1. Podpora pro spolupráci s COM bez registrace se mírně liší v závislosti na typu sestavení knihovny; Konkrétně, určuje, zda je nespravované (COM-souběžně) nebo spravované sestavení (. NET-based). V následující tabulce jsou uvedeny operační systém a požadavky na verzi rozhraní .NET Framework pro každý typ sestavení.  
  
    |Typ sestavení|Operační systém|Verze rozhraní .NET Framework|  
    |-------------------|----------------------|----------------------------|  
    |COM –-vedle sebe|Microsoft Windows XP|Není nutné.|  
    |. Na základě NET|Windows XP s aktualizací SP2|.NET Framework verze 1.1 nebo novější.|  
  
     Řady Windows Server 2003 také podporuje interoperabilitu COM bez registrace pro. Na základě NET sestavení.  
  
     Pro. Na základě NET třídě může být kompatibilní s aktivace registru z modelu COM, třídě musí mít výchozí konstruktor a musí být veřejné.  
  
### <a name="configuring-com-components-for-registration-free-activation"></a>Konfigurace komponent COM pro aktivaci bez registrace  
  
1. Pro komponenty modelu COM pro podílet na aktivaci bez registrace musí být nasazený jako sestavení vedle sebe. Nespravované sestavení jsou sestavení vedle sebe.  Další informace najdete v tématu [sestavení vedle sebe](/windows/desktop/SbsCs/using-side-by-side-assemblies).  
  
     Použít sestavení vedle sebe modelu COM,. Vývojář aplikace založené na NET musí poskytnout manifest aplikace, který obsahuje informace o vazbě a aktivace. Operační systém Windows XP obsahuje integrovanou podporu pro nespravované sestavení vedle sebe. Modul runtime modelu COM podporuje operační systém, prohledá manifest aplikace pro informace o aktivaci při komponenty, aktivuje se nenachází v registru.  
  
     Aktivace bez registrace je volitelný pro komponenty modelu COM, které jsou nainstalované na Windows XP. Podrobné pokyny pro přidání sestavení vedle sebe do aplikace najdete v tématu [sestavení vedle sebe](/windows/desktop/SbsCs/using-side-by-side-assemblies).  
  
    > [!NOTE]
    >  Vedle sebe spuštění je funkce rozhraní .NET Framework, která umožňuje více verzí modulu runtime a více verzí aplikací a komponent, které používají verzi modulu runtime, spustit současně na stejném počítači. Spuštění vedle sebe a sestavení vedle sebe jsou různé mechanismy pro zajištění funkcí vedle sebe.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Konfigurace Bezregistrační aktivace komponent COM založené na platformě .NET](../../../docs/framework/interop/configure-net-framework-based-com-components-for-reg.md)
