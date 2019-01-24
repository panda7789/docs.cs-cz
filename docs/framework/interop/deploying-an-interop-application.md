---
title: Nasazení aplikace spolupráce
ms.date: 03/30/2017
helpviewer_keywords:
- deploying applications [.NET Framework], interop
- strong-named assemblies, interop applications
- unsigned assemblies
- private assemblies
- exposing COM components to .NET Framework
- interoperation with unmanaged code, deploying applications
- shared assemblies
- COM interop, deploying applications
- interoperation with unmanaged code, exposing COM components
- signed assemblies
- COM interop, exposing COM components
ms.assetid: ea8a403e-ae03-4faa-9d9b-02179ec72992
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e74e4784d295e46972e10c5b9e1d4cc4bafa944
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496764"
---
# <a name="deploying-an-interop-application"></a>Nasazení aplikace spolupráce
Spolupráce aplikace obvykle obsahují sestavení klienta .NET, jeden nebo více sestavení vzájemné spolupráce představující odlišné COM knihoven typů a jedna nebo více komponent COM registrovány. Visual Studio a [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] poskytují nástroje pro import a převod knihovny typů do sestavení vzájemné spolupráce, jak je popsáno v [importování knihovny typů jako sestavení](importing-a-type-library-as-an-assembly.md). Nasazení aplikace spolupráce dvěma způsoby:  
  
-   Pomocí vestavěné typy spolupráce: Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], můžete dát pokyn kompilátoru k vložení informací o typu ze sestavení vzájemné spolupráce do spustitelného souboru. Kompilátor vloží jenom informace o typu, který vaše aplikace používá. Není nutné k nasazení sestavení vzájemné spolupráce s vaší aplikací. Toto je doporučený postup.  
  
-   Nasazením sestavení vzájemné spolupráce: Můžete vytvořit standardní odkaz na sestavení vzájemné spolupráce. V takovém případě musí být nasazeny sestavení zprostředkovatele komunikace s vaší aplikací. Pokud nepoužijete tento postup a nepoužíváte Soukromá komponenta modelu COM, vždycky odkazujte na sestavení primární spolupráce (PIA) publikoval Autor komponenty modelu COM, které chcete začlenit ve spravovaném kódu. Další informace o vytváření a používání sestavení primární spolupráce naleznete v tématu [Primary Interop Assemblies](https://msdn.microsoft.com/library/b977a8be-59a0-40a0-a806-b11ffba5c080(v=vs.100)).  
  
 Pokud používáte vestavěné typy spolupráce, nasazení je jednoduché a nekomplikované. Není nic zvláštního, že je třeba provést. Zbývající část tohoto článku popisuje scénáře pro nasazení sestavení vzájemné spolupráce s vaší aplikací.  
  
## <a name="deploying-interop-assemblies"></a>Nasazení sestavení vzájemné spolupráce  
 Sestavení může mít silné názvy. Sestavení se silným názvem obsahuje veřejný klíč vydavatele, který poskytuje jedinečnou identitu. Sestavení, které jsou vytvářeny [Importér knihovny typů (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) můžete pomocí podepsané vydavatelem **/keyfile** možnost. Podepsaná sestavení můžete nainstalovat do globální mezipaměti sestavení. Nepodepsaná sestavení musí být nainstalována na počítač uživatele jako soukromá sestavení.  
  
### <a name="private-assemblies"></a>Soukromá sestavení  
 Chcete-li nainstalovat sestavení, které chcete použít soukromě, musí být nainstalovaná spustitelný soubor aplikace a sestavení vzájemné spolupráce, který obsahuje importované typy modelu COM ve stejné struktuře adresářů. Následující obrázek znázorňuje bez znaménka definiční sestavení použije soukromě Client1.exe a Client2.exe, které jsou umístěny v adresářích samostatné aplikace. Definiční sestavení, která se nazývá LOANLib.dll v tomto příkladu, je nainstalována dvakrát.  
  
 ![Adresářovou strukturu a registru Windows](media/comdeployprivate.gif "comdeployprivate")  
Adresář položky struktury a registru pro privátní nasazení  
  
 Všechny komponenty modelu COM, které jsou přidružené k aplikaci musí být nainstalován v registru Windows. Pokud Client1.exe a Client2.exe na obrázku jsou nainstalované na různých počítačích, budete muset zaregistrovat komponenty modelu COM na obou počítačích.  
  
### <a name="shared-assemblies"></a>Sdílená sestavení  
 Sestavení, které jsou sdíleny více aplikací musí být nainstalován v centrálním úložišti názvem do globální mezipaměti sestavení. .NET klienti mají přístup k stejnou kopii definiční sestavení, která je podepsaná a nainstalované v globální mezipaměti sestavení. Další informace o vytváření a používání sestavení primární spolupráce naleznete v tématu [Primary Interop Assemblies](https://msdn.microsoft.com/library/b977a8be-59a0-40a0-a806-b11ffba5c080(v=vs.100)).  
  
## <a name="see-also"></a>Viz také:
- [Vystavení komponent COM pro rozhraní .NET Framework](exposing-com-components.md)
- [Import knihovny typů ve formě sestavení](importing-a-type-library-as-an-assembly.md)
- [Používání typů modelu COM ve spravovaném kódu](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100))
- [Kompilace projektu interoperability](compiling-an-interop-project.md)
