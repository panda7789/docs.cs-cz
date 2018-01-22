---
title: "Postupy: Generování primárních sestavení vzájemné spolupráce pomocí Tlbimp.exe"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- primary interop assemblies, generating
- Tlbimp.exe
- Type Library Importer
ms.assetid: 5419011c-6e57-40f6-8c65-386db8f7a651
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4dfbf3c2282e60ec45cb136f52fb115a8d769678
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-generate-primary-interop-assemblies-using-tlbimpexe"></a>Postupy: Generování primárních sestavení vzájemné spolupráce pomocí Tlbimp.exe
Existují dva způsoby, jak vygenerovat primární spolupracující sestavení:  
  
-   Pomocí [zadejte Importér knihovny (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) poskytované [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].  
  
     Nejjednodušší způsob, jak můžete vytvořit primární spolupracující sestavení se má používat [Tlbimp.exe (Importér knihovny)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md). Tlbimp.exe poskytuje následující bezpečnostní opatření:  
  
    -   Zkontroluje ostatní registrované primární spolupracující sestavení před vytvořením nového sestavení vzájemné spolupráce pro všechny vnořené typy knihovny odkazy.  
  
    -   Pokud nezadáte buď kontejner, nebo název souboru umožnit primární spolupracující sestavení silným názvem generování primárních sestavení vzájemné spolupráce se nezdaří.  
  
    -   Emitování primárních sestavení vzájemné spolupráce, pokud vynecháte odkazy na závislé sestavení se nezdaří.  
  
    -   Emitování primárních sestavení vzájemné spolupráce, pokud přidáte odkazy na závislé sestavení, které nejsou primární spolupracující sestavení se nezdaří.  
  
-   Primární spolupracující sestavení ruční vytváření ve zdrojovém kódu pomocí jazyka, který je kompatibilní s specifikace CLS (Common Language), například C#. Tento přístup je užitečné, když není k dispozici knihovny typů.  
  
 Musíte mít páru kryptografických klíčů k podepsání sestavení silným názvem. Podrobnosti najdete v tématu [vytvoření páru klíč A](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).  
  
### <a name="to-generate-a-primary-interop-assembly-using-tlbimpexe"></a>Ke generování primárních sestavení vzájemné spolupráce pomocí Tlbimp.exe  
  
1.  V příkazovém řádku zadejte příkaz:  
  
     **Tlbimp** *tlbfile***/primární/keyfile:** *filename* **/out:** *assemblyname*   
  
     V tomto příkazu *tlbfile* je soubor obsahuje knihovnu typů COM *filename* je název kontejneru nebo soubor, který obsahuje pár klíčů a *assemblyname* je název sestavení se silným názvem přihlásit.  
  
 Primární spolupracující sestavení může odkazovat jenom jiné primární spolupracující sestavení. Pokud vaše sestavení odkazuje typy z knihovny typů COM třetích stran, musíte získat primární spolupracující sestavení od vydavatele, než může generovat vaší primární spolupracující sestavení. Pokud jste vydavatele, musíte vygenerovat primární spolupracující sestavení pro knihovnu závislého typu před vygenerováním odkazující sestavení primární spolupráce.  
  
 Závislé sestavení primární spolupráce s číslem verze, která se liší od původního knihovny typů není zjistitelný při instalaci v aktuálním adresáři. Musíte zaregistrovat závislé sestavení primární spolupráce v registru systému Windows nebo pomocí **/reference** možnost Ujistěte se, že vyhledá Tlbimp.exe závislé knihovny DLL.  
  
 Můžete také zabalit několik verzí knihovny typů. Pokyny najdete v tématu [postupy: zabalení více verzí z knihovny typů](http://msdn.microsoft.com/library/79eefe04-a770-4bc3-8ea2-e90ddb8ec31f).  
  
## <a name="example"></a>Příklad  
 Následující příklad importuje knihovny typů COM `LibUtil.tlb` a podepisuje sestavení `LibUtil.dll` se silným názvem pomocí souboru klíče `CompanyA.snk`. Díky vynechání název konkrétní oboru názvů, tento příklad vytvoří výchozí obor názvů `LibUtil`.  
  
```  
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /out:LibUtil.dll  
```  
  
 Pro více popisný název (pomocí *poznámky:*. *NázevKnihovny* pojmenování platí), tento příklad přepíše výchozí název souboru sestavení a název oboru názvů.  
  
```  
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /namespace:CompanyA.LibUtil /out:CompanyA.LibUtil.dll  
```  
  
 Následující příklad importuje `MyLib.tlb`, jehož odkazy `CompanyA.LibUtil.dll`, a podepisuje sestavení `CompanyB.MyLib.dll` se silným názvem pomocí souboru klíče `CompanyB.snk`. Obor názvů, `CompanyB.MyLib`, přepíše výchozí obor názvů.  
  
```  
tlbimp MyLib.tlb /primary /keyfile:CompanyB.snk /namespace:CompanyB.MyLib /reference:CompanyA.LibUtil.dll /out:CompanyB.MyLib.dll  
```  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Registrace primárních sestavení spolupráce](../../../docs/framework/interop/how-to-register-primary-interop-assemblies.md)
