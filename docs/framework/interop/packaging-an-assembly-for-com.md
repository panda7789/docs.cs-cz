---
title: "Zabalení sestavení pro model COM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, packaging assemblies
- packaging assemblies for COM
- Tlbexp.exe
- TypeLibConverter class
- .NET Services Installation tool
- Assembly Registration tool
- Type Library Exporter
- Reqsvcs.exe
- interoperation with unmanaged code, exposing .NET Framework components
- interoperation with unmanaged code, packaging assemblies
- COM interop, exposing COM components
- Reqasm.exe
ms.assetid: 39dc55aa-f2a1-4093-87bb-f1c0edb6e761
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 79c0d8ff3d6f66ad3abf23cd371f86bb74edf78e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="packaging-an-assembly-for-com"></a>Zabalení sestavení pro model COM
COM vývojáři mohou využít následující informace o spravovaných typů, že chtějí začlenit ve svých aplikacích:  
  
-   Seznam typů, které můžou využívat aplikace modelu COM  
  
     Některé spravované typy jsou neviditelná pro COM; Některé jsou viditelné, ale není vytvořitelné; a některé jsou viditelné a vytvořitelné. Sestavení může obsahovat libovolnou kombinaci typů neviditelná, viditelné, není vytvořitelné a vytvořitelné. Pro úplnost Identifikujte typy v sestavení, které máte v úmyslu umístěte do modelu COM, zejména v případě, že tyto typy jsou podmnožinou typy vystavený rozhraní .NET Framework.  
  
     Další informace najdete v tématu [kvalifikace typů .NET pro spolupráci](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md).  
  
-   Správa verzí pokyny  
  
     Spravované třídy, které implementují rozhraní třídy (rozhraní modelu COM generované zprostředkovatel komunikace s objekty) se vztahují omezení Správa verzí.  
  
     Na pomocí třídy rozhraní, naleznete na adrese [představení rozhraní třídy](http://msdn.microsoft.com/library/733c0dd2-12e5-46e6-8de1-39d5b25df024).  
  
-   Pokyny k nasazení  
  
     Sestavení se silným názvem, které jsou podepsané vydavatelem lze nainstalovat do globální mezipaměti sestavení. Nepodepsaná sestavení musí být nainstalován na počítači uživatele jako soukromá sestavení.  
  
     Další informace najdete v tématu [důležité informace o zabezpečení sestavení](../../../docs/framework/app-domains/assembly-security-considerations.md).  
  
-   Zahrnutí knihovny typů  
  
     Většina typů vyžadují knihovny typů při spotřebovávají aplikace modelu COM. Můžete vygenerovat knihovny typů nebo mít COM vývojáři provedení této úlohy. [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Poskytuje následující možnosti pro generování knihovny typů:  
  
    -   [Knihovna typů – Exportér](#cpconpackagingassemblyforcomanchor1)  
  
    -   [TypeLibConverter – třída](#cpconpackagingassemblyforcomanchor2)  
  
    -   [Registrace sestavení – nástroj](#cpconpackagingassemblyforcomanchor3)  
  
    -   [Nástroj pro instalaci služeb .NET](#cpconpackagingassemblyforcomanchor4)  
  
     Bez ohledu na to mechanismus, který zvolíte jsou zahrnuty pouze veřejné typy definované v sestavení, ve kterém zadáte v knihovně generovaného typu.  
  
     Můžete balíček knihovny typů jako samostatný soubor nebo vložit jako zdrojového souboru Win32 v rámci. Aplikace založené na Asp.net. Microsoft Visual Basic 6.0 provést tuto úlohu pro vás automaticky. ale při použití [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)], je nutné ručně vložit vaší knihovny typů. Pokyny najdete v tématu [postupy: vložení knihovny typů jako Win32 prostředky v. Aplikace založené na NET](http://msdn.microsoft.com/library/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44).  
  
<a name="cpconpackagingassemblyforcomanchor1"></a>   
## <a name="type-library-exporter"></a>knihovna typů – exportér  
 [Exportér knihovny typů (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) je nástroj příkazového řádku, který převádí třídy a rozhraní, které jsou součástí sestavení pro knihovny typů COM. Jakmile informace o typu třídy je k dispozici, klienti COM můžete vytvořit instance třídy rozhraní .NET a volání metody instance, stejně, jako by šlo objektu COM. Tlbexp.exe převede celé sestavení najednou. Pomocí nástroje Tlbexp.exe nelze generovat informace o typu pro podtypy definované v sestavení.  
  
<a name="cpconpackagingassemblyforcomanchor2"></a>   
## <a name="typelibconverter-class"></a>TypeLibConverter – třída  
 <xref:System.Runtime.InteropServices.TypeLibConverter> Třídy, které jsou umístěné v **System.Runtime.Interop** převede obor názvů, třídy a rozhraní, které jsou součástí sestavení pro knihovny typů COM. Toto rozhraní API vytváří stejný typ informace jako Export knihovny typů popsané v předchozí části.  
  
 **TypeLibConverter – třída** implementuje <xref:System.Runtime.InteropServices.ITypeLibConverter>.  
  
<a name="cpconpackagingassemblyforcomanchor3"></a>   
## <a name="assembly-registration-tool"></a>Registrace sestavení – nástroj  
 [Nástroj pro registraci sestavení (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) vygenerovat a registraci knihovny typů, při použití **/tlb:** možnost. Klienti COM vyžadují instalaci knihovny typů v registru systému Windows. Bez této možnosti Regasm.exe pouze registruje typy v sestavení, není knihovny typů. Registrace typy v sestavení a registraci knihovny typů jsou odlišné aktivity.  
  
<a name="cpconpackagingassemblyforcomanchor4"></a>   
## <a name="net-services-installation-tool"></a>Nástroj pro instalaci služeb .NET  
 [Nástroj pro instalaci služeb .NET (Regsvcs.exe)](../../../docs/framework/tools/regsvcs-exe-net-services-installation-tool.md) přidá spravované třídy do služby součásti systému Windows 2000 a kombinuje několik úkolů v rámci jediného nástroje. Kromě načítání a registraci sestavení, Regsvcs.exe generovat, zaregistrujte a nainstalovat do existující aplikace COM + 1.0 knihovny typů.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.TypeLibConverter>  
 <xref:System.Runtime.InteropServices.ITypeLibConverter>  
 [Vystavení komponent architektury .NET Framework pro COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [Kvalifikace typů .NET pro spolupráci](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md)  
 [Představení rozhraní – třída](http://msdn.microsoft.com/library/733c0dd2-12e5-46e6-8de1-39d5b25df024)  
 [Důležité informace o zabezpečení sestavení](../../../docs/framework/app-domains/assembly-security-considerations.md)  
 [Tlbexp.exe (exportér knihovny typů)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)  
 [Registrování sestav pomocí modelu COM](../../../docs/framework/interop/registering-assemblies-with-com.md)  
 [Postupy: vložení knihovny typů jako Win32 prostředky v aplikacích](http://msdn.microsoft.com/library/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44)
