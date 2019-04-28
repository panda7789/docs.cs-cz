---
title: 'Postupy: Generování primárních sestavení vzájemné spolupráce pomocí Tlbimp.exe'
ms.date: 03/30/2017
helpviewer_keywords:
- primary interop assemblies, generating
- Tlbimp.exe
- Type Library Importer
ms.assetid: 5419011c-6e57-40f6-8c65-386db8f7a651
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a944cf87783c59c21bffc9c48a18237c9fe6cdec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61643228"
---
# <a name="how-to-generate-primary-interop-assemblies-using-tlbimpexe"></a>Postupy: Generování primárních sestavení vzájemné spolupráce pomocí Tlbimp.exe
Existují dva způsoby, jak vygenerovat primární spolupracující sestavení:  
  
- Použití [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) poskytované [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].  
  
     Nejjednodušší způsob, jak vytvořit primárních sestavení vzájemné spolupráce je použít [Tlbimp.exe (Importér knihovny typů)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md). Tlbimp.exe obsahuje následující bezpečnostní opatření:  
  
    - Vyhledá další registrovaných primárních spolupracujících sestavení před vytvořením nového sestavení vzájemné spolupráce pro všechny odkazy na knihovnu vnořeného typu.  
  
    - Pokud nezadáte, kontejneru nebo souboru název primárního spolupracujícího sestavení silným názvem generování primárních sestavení vzájemné spolupráce se nezdaří.  
  
    - Generování primárních sestavení vzájemné spolupráce vynecháte odkazy na závislé sestavení se nezdaří.  
  
    - Generování primárního spolupracujícího sestavení, pokud přidáte odkazy na závislé sestavení, které nejsou primární spolupracující sestavení se nezdaří.  
  
- Ruční vytváření primárních sestavení vzájemné spolupráce ve zdrojovém kódu pomocí jazyka, který je kompatibilní s specifikace CLS (Common Language), jako například C#. Tento přístup je užitečný, pokud knihovna typů není k dispozici.  
  
 Musíte mít pár kryptografických klíčů k podepsání sestavení silným názvem. Podrobnosti najdete v tématu [vytváření dvojice klíč A](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).  
  
### <a name="to-generate-a-primary-interop-assembly-using-tlbimpexe"></a>Chcete-li vygenerovat primární sestavení vzájemné spolupráce pomocí Tlbimp.exe  
  
1. V příkazovém řádku zadejte příkaz:  
  
     **Tlbimp** *tlbfile***/primary/keyfile:** *filename* **/out:** *assemblyname*  
  
     V tomto příkazu *tlbfile* je soubor, který obsahuje knihovnu typů modelu COM *filename* je název kontejneru nebo souboru, který obsahuje pár klíčů a *assemblyname* je název sestavení podepsáno pomocí silného názvu.  
  
 Primární spolupracující sestavení může odkazovat jenom jiných primárních sestavení vzájemné spolupráce. Pokud vaše sestavení používá odkazy na typy v knihovně typů modelu COM třetích stran, musíte získat primární spolupracující sestavení od vydavatele předtím, než můžete vygenerovat primární definiční sestavení. Pokud jste vydavatel, budete muset vygenerovat primární spolupracující sestavení pro závislou typovou knihovnu před generováním odkazující sestavení primární spolupráce.  
  
 Závislé primárního spolupracujícího sestavení s číslem verze, která se liší od původní knihovna typů není zjistitelné při instalaci v aktuálním adresáři. Musíte zaregistrovat závislé sestavení primární spolupráce v registru Windows nebo použít **/reference** možnost, abyste měli jistotu, že Tlbimp.exe najde závislá knihovna DLL.  
  
 Můžete také zabalit několik verzí knihovny typů. Pokyny najdete v tématu [jak: Sbalení více verzí knihoven typů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/1565h6hc(v=vs.100)).  
  
## <a name="example"></a>Příklad  
 Následující příklad importuje knihovna typů COM `LibUtil.tlb` a podepíše sestavení `LibUtil.dll` se silným názvem pomocí souboru s klíči `CompanyA.snk`. Vynecháním názvu konkrétní obor názvů, tento příklad vytvoří výchozí obor názvů `LibUtil`.  
  
```  
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /out:LibUtil.dll  
```  
  
 Pro více popisný název (pomocí *podporovány*. *NázevKnihovny* pojmenování obecných zásad), tento příklad přepíše výchozí název souboru sestavení a název oboru názvů.  
  
```  
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /namespace:CompanyA.LibUtil /out:CompanyA.LibUtil.dll  
```  
  
 Následující příklad importuje `MyLib.tlb`, který se odkazuje na `CompanyA.LibUtil.dll`, a podepíše sestavení `CompanyB.MyLib.dll` se silným názvem pomocí souboru s klíči `CompanyB.snk`. Obor názvů, `CompanyB.MyLib`, přepíše výchozí název oboru názvů.  
  
```  
tlbimp MyLib.tlb /primary /keyfile:CompanyB.snk /namespace:CompanyB.MyLib /reference:CompanyA.LibUtil.dll /out:CompanyB.MyLib.dll  
```  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Registrace primárních sestavení spolupráce](../../../docs/framework/interop/how-to-register-primary-interop-assemblies.md)
