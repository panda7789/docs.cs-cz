---
title: Zařazování dat se spoluprací COM
ms.date: 09/07/2017
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
ms.openlocfilehash: ae41713d5349321725599c0c38d7c6fc515c374b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181376"
---
# <a name="marshaling-data-with-com-interop"></a>Zařazování dat se spoluprací COM
Com interop poskytuje podporu pro použití objektů COM ze spravovaného kódu a vystavení spravovaných objektů com. Podpora pro zařazování dat do a z COM je rozsáhlá a téměř vždy poskytuje správné zařazování chování.  
  
 Sada Windows SDK obsahuje následující nástroje pro propojení COM:  
  
- [Importknihovny typů (Tlbimp.exe),](../tools/tlbimp-exe-type-library-importer.md)který převede knihovnu typů COM na interop sestavení. Z tohoto sestavení interop zařazování služba generuje obálky, které provádějí zařazování dat mezi spravované a nespravované paměti.  
  
- [Typ knihovny Exportér (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md), který vytváří knihovnu typu COM ze sestavení a generuje obálku, která provádí zařazování během volání metody.  
  
 Následující části odkazují na témata, která popisují procesy pro přizpůsobení obálky meziop, pokud můžete (nebo musíte) poskytnout zařazovací zařízení další informace o typu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
[Postup: Ruční vytvoření obalů](how-to-create-wrappers-manually.md) Popisuje, jak ručně vytvořit obálku com ve spravovaném zdrojovém kódu.

 [Postup: Migrace spravovaného kódu DCOM do WCF](how-to-migrate-managed-code-dcom-to-wcf.md)  
 Popisuje, jak migrovat spravovaný kód DCOM do WCF pro nejbezpečnější řešení.  
  
## <a name="related-sections"></a>Související oddíly  
 [Datové typy COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))  
 Poskytuje odpovídající spravované a nespravované datové typy.  
  
 [Přizpůsobení com callable obálky](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))  
 Popisuje, jak explicitně zařazovat datové typy pomocí atributu <xref:System.Runtime.InteropServices.MarshalAsAttribute> v době návrhu.  
  
 [Přizpůsobení reložií s runtime voláním](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))  
 Popisuje, jak upravit zařazování chování typů v sestavení interop a jak definovat typy COM ručně.  
  
 [Pokročilá interoperabilita com](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))  
 Obsahuje odkazy na další informace o začlenění komponent modelu COM do aplikace rozhraní .NET Framework.  
  
 [Souhrn převodu knihovny sestavení k typu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))  
 Popisuje sestavení, které má být napsáno, aby byl proces převodu exportu knihovny zadán.  
  
 [Souhrn převodu knihovny typů do sestavení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))  
 Popisuje knihovnu typů pro proces převodu převodu sestavení.  
  
 [Spolupráce pomocí obecných typů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))  
 Popisuje, které akce jsou podporovány při použití obecných typů pro interoperabilitu com.
