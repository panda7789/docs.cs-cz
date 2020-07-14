---
title: Zprostředkovatel komunikace s objekty COM bez registrace
description: K aktivaci komponenty bez použití registru Windows k ukládání informací o sestavení použijte zprostředkovatele komunikace COM bez registrace.
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
ms.openlocfilehash: c6a4dfc54152ade6136e4292bbd1c4522553d491
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281599"
---
# <a name="registration-free-com-interop"></a>Zprostředkovatel komunikace s objekty COM bez registrace
Zprostředkovatel komunikace s objekty COM bez registrace aktivuje komponentu bez použití registru Windows k ukládání informací o sestavení. Místo registrace komponenty v počítači během nasazení vytvoříte v době návrhu soubory manifestu ve stylu Win32, které obsahují informace o vazbách a aktivaci. Tyto soubory manifestu, nikoli klíče registru, nasměrují aktivaci objektu.  
  
 Použití aktivace bez registrace pro vaše sestavení místo jejich registrace během nasazení nabízí dvě výhody:  
  
- Můžete řídit, která verze knihovny DLL je aktivována, pokud je v počítači nainstalována více než jedna verze.  
  
- Koncoví uživatelé můžou pomocí příkazu XCOPY nebo FTP zkopírovat aplikaci do příslušného adresáře na svém počítači. Aplikaci lze následně spustit z tohoto adresáře.  
  
 Tato část popisuje dva typy manifestů, které jsou potřeba pro zprostředkovatele komunikace s objekty COM bez registrace: manifesty aplikací a komponent. Tyto manifesty jsou soubory XML. Manifest aplikace, který je vytvořen vývojářem aplikace, obsahuje metadata, která popisují sestavení a závislosti sestavení. Manifest komponenty vytvořený vývojářem komponent obsahuje informace, které jsou v registru systému Windows jiné.  
  
### <a name="requirements-for-registration-free-com-interop"></a>Požadavky na zprostředkovatele komunikace s objekty COM bez registrace  
  
1. Podpora komunikace s objekty COM bez registrace se mírně liší v závislosti na typu sestavení knihovny; konkrétně bez ohledu na to, zda je sestavení nespravované (souběžně) nebo spravované (. Založené na síti. V následující tabulce jsou uvedeny požadavky na operační systém a .NET Framework verze pro každý typ sestavení.  
  
    |Typ sestavení|Operační systém|Verze rozhraní .NET Framework|  
    |-------------------|----------------------|----------------------------|  
    |COM vedle sebe|Microsoft Windows XP|Nepožadováno.|  
    |. Založený na síti|Windows XP s aktualizací SP2|Rozhraní .NET Framework verze 1,1 nebo novější.|  
  
     Řada Windows Server 2003 také podporuje zprostředkovatele komunikace COM bez registrace pro. Sestavení založená na síti.  
  
     Pro. Třída založená na síti, která bude kompatibilní s aktivací bez registru z modelu COM, musí mít konstruktor bez parametrů a musí být veřejná.  
  
### <a name="configuring-com-components-for-registration-free-activation"></a>Konfigurace komponent modelu COM pro aktivaci bez registrace  
  
1. Aby komponenta modelu COM mohla být součástí aktivace bez registrace, musí být nasazena jako souběžné sestavení. Souběžná sestavení jsou nespravovaná sestavení.  Další informace najdete v tématu [použití souběžných sestavení](/windows/desktop/SbsCs/using-side-by-side-assemblies).  
  
     Chcete-li použít sestavení souběžně na straně modelu COM,. Vývojář aplikací založených na síti musí poskytovat manifest aplikace, který obsahuje informace o vazbě a aktivaci. Podpora nespravovaných sestavení souběžně na straně je integrovaná do operačního systému Windows XP. Modul runtime COM podporovaný operačním systémem vyhledá v manifestu aplikace informace o aktivaci, když je součást aktivovaná v registru.  
  
     Aktivace bez registrace je volitelná pro komponenty modelu COM nainstalované v systému Windows XP. Podrobné pokyny týkající se přidání souběžného sestavení do aplikace najdete v tématu [použití souběžných sestavení](/windows/desktop/SbsCs/using-side-by-side-assemblies).  
  
    > [!NOTE]
    > Souběžné spouštění je funkce .NET Framework, která umožňuje více verzí modulu runtime a více verzí aplikací a komponent, které používají verzi modulu runtime, pro spuštění ve stejném počítači současně. Souběžné spouštění a souběžná sestavení jsou různými mechanismy pro poskytování funkcí vedle sebe.  
  
## <a name="see-also"></a>Viz také

- [Postupy: Konfigurace komponent COM využívajících rozhraní .NET Framework pro aktivaci bez registrace](configure-net-framework-based-com-components-for-reg.md)
