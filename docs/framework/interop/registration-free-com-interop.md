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
ms.openlocfilehash: 32ee3babe054d55a45cc8826843252dba6aa2be7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="registration-free-com-interop"></a>Zprostředkovatel komunikace s objekty COM bez registrace
Spoluprací COM bez registrace se aktivuje komponentu bez uložení informací o sestavení pomocí registru systému Windows. Místo registrace komponenty v počítači během nasazení, vytvoření souborů manifestu Win32 stylu v době návrhu, které obsahují informace o aktivaci a vazeb. Tyto soubory manifestu, nikoli klíče registru přímé aktivace objektu.  
  
 Použití bezregistrační aktivace pro vaše sestavení místo registrace je během nasazení nabízí dvě výhody:  
  
-   Můžete řídit, které DLL verze knihovny se aktivuje, když více než jedna verze je nainstalovaná na počítači.  
  
-   Koncoví uživatelé mohou používat XCOPY nebo FTP zkopírovat vaší aplikace do příslušného adresáře v počítači. Aplikace pak spustíte z tohoto adresáře.  
  
 Tato část popisuje dva typy manifesty potřeba pro spolupráci s COM bez registrace: manifestů aplikace a součásti. Tyto manifesty jsou soubory formátu XML. Manifest aplikace, který je vytvořen vývojář aplikací, obsahuje metadata, která popisuje sestavení a závislosti sestavení. Manifest součásti, vytvořené vývojář součást obsahuje informace, v opačném případě umístěny v registru systému Windows.  
  
### <a name="requirements-for-registration-free-com-interop"></a>Požadavky pro spolupráci s COM bez registrace  
  
1.  Podpora pro spoluprací COM bez registrace se mírně liší v závislosti na typu knihovny sestavení; Konkrétně, jestli je nespravované (COM-souběžného) nebo spravované sestavení (. NET-based). V následující tabulce jsou uvedeny operačního systému a požadavky na verzi rozhraní .NET Framework pro každý typ sestavení.  
  
    |Typ sestavení|Operační systém|Verze rozhraní .NET Framework|  
    |-------------------|----------------------|----------------------------|  
    |COM – souběžného|Microsoft Windows XP|Není požadováno.|  
    |. Na základě NET|Windows XP s aktualizací SP2|NET Framework verze 1.1 nebo novější.|  
  
     Řady Windows Server 2003 podporuje také spoluprací COM bez registrace pro. Na základě NET sestavení.  
  
     Pro. Na základě NET třída být kompatibilní s registru bez aktivace z modelu COM, třídu musí mít výchozí konstruktor a musí být veřejné.  
  
### <a name="configuring-com-components-for-registration-free-activation"></a>Konfigurace komponenty modelu COM bez registrace aktivace  
  
1.  Pro komponenty modelu COM se účastnit bezregistrační aktivace musí být nasazený jako souběžně sdílená sestavení. Souběžně sdílená sestavení jsou nespravované sestavení.  Další informace najdete v tématu [pomocí souběžně sdílená sestavení](https://msdn.microsoft.com/library/windows/desktop/aa376618.aspx).  
  
     Chcete-li používat souběžně sdílená sestavení COM,. Aplikace založené na NET vývojář musí poskytnout manifest aplikace, který obsahuje informace o aktivaci a vazeb. Podpora pro nespravovaná souběžně sdílená sestavení je integrovaná do operačního systému Windows XP. Modul runtime COM, nepodporuje operační systém, prohledává manifest aplikace pro informace o aktivaci k aktivované součást není v registru.  
  
     Bezregistrační aktivace je volitelný pro komponenty modelu COM, které jsou nainstalované v systému Windows XP. Podrobné pokyny k přidání souběžně sdílená sestavení do aplikace, najdete v části [pomocí souběžně sdílená sestavení](https://msdn.microsoft.com/library/windows/desktop/aa376618.aspx).  
  
    > [!NOTE]
    >  Souběžného zpracování se funkce rozhraní .NET Framework, která umožňuje více verzí modulu runtime a více verzí aplikací a součástí, které používají verzi modulu runtime ve stejnou dobu běžela na stejném počítači. Spuštění vedle sebe a souběžně sdílená sestavení jsou různé mechanismy pro zajištění funkcí vedle sebe.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Konfigurace bezregistrační aktivace komponent využívajících rozhraní .NET Framework](../../../docs/framework/interop/configure-net-framework-based-com-components-for-reg.md)
