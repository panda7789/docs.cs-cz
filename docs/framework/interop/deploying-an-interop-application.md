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
ms.openlocfilehash: d4689c52dee84e2a310f0ddb39d0874c273081bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="deploying-an-interop-application"></a>Nasazení aplikace spolupráce
Spolupráce aplikace obvykle zahrnuje klientského sestavení .NET, jeden nebo více sestavení vzájemné spolupráce představující odlišné COM knihovny typů a jeden nebo více registrované komponenty modelu COM. Visual Studio a [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] poskytují nástroje pro import a převést knihovny typů spolupráce sestavení, jak je popsáno v [Import knihovny typů jako sestavení](importing-a-type-library-as-an-assembly.md). K nasazení aplikace spolupráce dvěma způsoby:  
  
-   Pomocí vestavěné typy spolupráce: od verze [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], můžete určit, aby kompilátoru pro vložení informací o typu ze sestavení spolupráce do spustitelného souboru. Kompilátor vloží pouze typ informace, které vaše aplikace používá. Nemusíte nasazovat sestavení vzájemné spolupráce s vaší aplikací. Toto je doporučený postup.  
  
-   Nasazením spolupráce – sestavení: můžete vytvořit standardní odkaz na sestavení spolupráce. V takovém případě musí být nasazený sestavení vzájemné spolupráce s vaší aplikací. Pokud nepoužijete tento postup a nepoužíváte privátní komponenty modelu COM, vždy referenční sestavení primární spolupráce (PIA), které zveřejnil Autor komponenty modelu COM, které chcete mít ve spravovaném kódu. Další informace o vytváření a používání primárních sestavení vzájemné spolupráce najdete v tématu [primární zprostředkovatel komunikace s objekty sestavení](https://msdn.microsoft.com/library/b977a8be-59a0-40a0-a806-b11ffba5c080(v=vs.100)).  
  
 Pokud používáte vestavěné typy spolupráce, nasazení je jednoduchá a přímočará. Není co speciální, že musíte udělat. Zbývající část tohoto článku popisuje scénáře pro nasazení sestavení vzájemné spolupráce s vaší aplikací.  
  
## <a name="deploying-interop-assemblies"></a>Nasazení sestavení spolupráce  
 Sestavení mohou mít silné názvy. Sestavení se silným názvem obsahuje veřejný klíč vydavatele, který poskytuje jedinečnou identitu. Sestavení, které vznikají pomocí funkcí [Importér knihovny typů (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) může být podepsané vydavatelem pomocí **/keyfile** možnost. Podepsaná sestavení můžete nainstalovat do globální mezipaměti sestavení. Nepodepsaná sestavení musí být nainstalován na počítači uživatele jako soukromá sestavení.  
  
### <a name="private-assemblies"></a>Privátní sestavení  
 Instalace sestavení, které chcete použít soukromě, musí být nainstalován spustitelný soubor aplikace i spolupráce sestavení, které obsahuje importované typy modelu COM v stejného adresářové struktury. Následující obrázek znázorňuje nepodepsané sestavení vzájemné spolupráce má být používána soukromě Client1.exe a Client2.exe, které jsou umístěny v adresářích samostatné aplikace. Sestavení vzájemné spolupráce, který se nazývá LOANLib.dll v tomto příkladu, je nainstalována dvakrát.  
  
 ![Adresářovou strukturu a registru systému Windows](media/comdeployprivate.gif "comdeployprivate")  
Struktura a registru položek adresáře pro privátní nasazení  
  
 Všechny komponenty modelu COM, které jsou přidružené k aplikaci musí být nainstalován v registru systému Windows. Pokud Client1.exe a Client2.exe na obrázku jsou nainstalovány na různých počítačích, je nutné zaregistrovat komponenty COM na obou počítačích.  
  
### <a name="shared-assemblies"></a>Sdílená sestavení  
 Sestavení, které jsou sdíleny více aplikací by měly být nainstalovány v centrálním úložišti názvem globální mezipaměti sestavení. Rozhraní .NET klienti mají přístup k stejnou kopii sestavení vzájemné spolupráce, který je podepsaný a nainstalované v globální mezipaměti sestavení. Další informace o vytváření a používání primárních sestavení vzájemné spolupráce najdete v tématu [primární zprostředkovatel komunikace s objekty sestavení](https://msdn.microsoft.com/library/b977a8be-59a0-40a0-a806-b11ffba5c080(v=vs.100)).  
  
## <a name="see-also"></a>Viz také  
 [Vystavení komponent COM pro rozhraní .NET Framework](exposing-com-components.md)  
 [Import knihovny typů ve formě sestavení](importing-a-type-library-as-an-assembly.md)  
 [Použití typy modelu COM ve spravovaném kódu](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100))  
 [Kompilace projektu interoperability](compiling-an-interop-project.md)
