---
title: Zařazování dat se spoluprací COM
ms.date: 09/07/2017
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab4dbdd0a69b158ff5c49949bee5089bd3fe095c
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56220530"
---
# <a name="marshaling-data-with-com-interop"></a>Zařazování dat se spoluprací COM
Komunikace s objekty COM poskytuje podporu pro používání objektů modelu COM ze spravovaného kódu i vystavení spravované objekty do modelu COM. Podpora zařazování dat do a z modelu COM je rozsáhlý a téměř vždy poskytuje správné chování zařazování.  
  
 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Obsahuje následující nástroje vzájemné spolupráce COM:  
  
-   [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), která převede knihovnu typů modelu COM pro definiční sestavení. Z tohoto sestavení zprostředkovatele komunikace s objekty zařazování služby generuje obálky, které provádějí data zařazování mezi spravovanými a nespravovanými paměti.  
  
-   [Exportér knihovny (Tlbexp.exe) zadejte](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), který vytvoří knihovnu typů modelu COM ze sestavení a generuje obálku, která provádí zařazování během volání metody.  
  
 Následující části odkaz na témata popisující procesy pro přizpůsobení spolupráce obálky, když je můžete (nebo musí) zadat zařazovací modul s informace o dalších typech.  
  
## <a name="in-this-section"></a>V tomto oddílu  
[Postupy: Ruční vytváření obálek](how-to-create-wrappers-manually.md)   
Popisuje, jak ručně vytvořit obálky COM ve spravovaném zdrojovém kódu. 
 
 [Postupy: Migrace spravovaného kódu DCOM do WCF](../../../docs/framework/interop/how-to-migrate-managed-code-dcom-to-wcf.md)  
 Popisuje postup migrace spravovaného kódu DCOM do WCF nejbezpečnější řešení.  
  
## <a name="related-sections"></a>Související oddíly  
 [Datové typy COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))  
 Poskytuje odpovídající spravované a nespravované datové typy.  
  
 [Přizpůsobení obálek volatelných aplikacemi COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))  
 Popisuje, jak explicitně zařazení pomocí datových typů <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut v době návrhu.  
  
 [Přizpůsobení obálek Volatelných za běhu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))  
 Popisuje, jak chcete-li upravit chování zařazování typů v sestavení vzájemné spolupráce a tom, jak definovat typy modelu COM ručně.  
  
 [Rozšířená interoperabilita modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))  
 Obsahuje odkazy na další informace o začlenění komponenty modelu COM do vaší aplikace rozhraní .NET Framework.  
  
 [Sestavení zadejte souhrn převodu knihovny](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))  
 Popisuje sestavení na typ procesu převodu export knihovny.  
  
 [Souhrn převodu sestavení knihovny typů na](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))  
 Popisuje knihovnu typů do sestavení procesu převodu při importování.  
  
 [Spolupráce pomocí obecných typů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))  
 Popisuje akce, které jsou podporovány při použití obecných typů pro interoperabilitu COM.
