---
title: Zařazování dat se spoluprací COM
ms.date: 09/07/2017
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d0d94223223568efe921af3a340815a966cc6c6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33388352"
---
# <a name="marshaling-data-with-com-interop"></a>Zařazování dat se spoluprací COM
Zprostředkovatel komunikace s objekty COM poskytuje podporu pro používání objektů COM ze spravovaného kódu i vystavení spravovaných objektů modelu COM. Podpora zařazování dat do a z modelu COM je rozsáhlá a poskytuje téměř vždy správné chování zařazování.  
  
 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Zahrnuje následující nástroje zprostředkovatele komunikace s objekty COM:  
  
-   [Zadejte Importér knihovny (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), která převede sestavení vzájemné spolupráce COM knihovny typů. Zprostředkovatel komunikace s objekty zařazování služby z tohoto sestavení generuje obálky, které provádějí dat – zařazování mezi spravovanými a nespravovanými paměti.  
  
-   [Zadejte Export knihovny (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), který vytváří knihovnu COM typu ze sestavení a generuje obálky, který provádí zařazování při volání metody.  
  
 V následujících částech propojit témata, která popisují procesy pro přizpůsobení spolupráce obálky při můžete (nebo musí) zadáte vláken s informací o další typu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
[Postupy: ruční vytváření obálek](how-to-create-wrappers-manually.md)   
Popisuje, jak ručně vytvořit obálky COM v spravované zdrojového kódu. 
 
 [Postup: Migrace spravovaného kódu DCOM do WCF](../../../docs/framework/interop/how-to-migrate-managed-code-dcom-to-wcf.md)  
 Popisuje postup migrace spravovaného kódu DCOM do WCF nejbezpečnější řešení.  
  
## <a name="related-sections"></a>Související oddíly  
 [COM datové typy](https://msdn.microsoft.com/library/sak564ww(v=vs.100).aspx)  
 Poskytuje odpovídající spravovanými a nespravovanými datové typy.  
  
 [COM – obálky s možností přizpůsobení](https://msdn.microsoft.com/library/3bwc828w(v=vs.100).aspx)  
 Popisuje, jak explicitně zařazování datové typy pomocí <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut v době návrhu.  
  
 [Běhové obálky s možností přizpůsobení](https://msdn.microsoft.com/library/e753eftz(v=vs.100).aspx)  
 Popisuje, jak upravit chování zařazování typy v sestavení spolupráce a jak definovat typy modelu COM ručně.  
  
 [Interoperabilita modelů COM Upřesnit](https://msdn.microsoft.com/library/bd9cdfyx(v=vs.100).aspx)  
 Obsahuje odkazy na další informace o zahrnutí komponenty modelu COM do své aplikace rozhraní .NET Framework.  
  
 [Sestavení na typ souhrn konverze knihovny](https://msdn.microsoft.com/library/xk1120c3(v=vs.100).aspx)  
 Popisuje sestavení na typ procesu převodu export knihovny.  
  
 [Knihovny typů pro souhrn konverze sestavení](https://msdn.microsoft.com/library/k83zzh38(v=vs.100).aspx)  
 Popisuje knihovny typů pro převod importu sestavení.  
  
 [Spolupráce pomocí obecných typů](https://msdn.microsoft.com/library/ms229590(v=vs.100).aspx)  
 Popisuje akce, které jsou podporovány při použití obecných typů pro interoperabilita modelů COM.
