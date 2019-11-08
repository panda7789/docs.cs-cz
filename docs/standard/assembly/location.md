---
title: Umístění sestavení
ms.date: 08/20/2019
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
ms.openlocfilehash: 0b84aba749625f0f86027cd9d09a5e9a2229a3f2
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733123"
---
# <a name="assembly-location"></a>Umístění sestavení
Umístění sestavení Určuje, zda se modul CLR (Common Language Runtime) může při odkazování najít a může také určit, zda může být sestavení sdíleno s jinými sestaveními. Sestavení můžete nasadit v následujících umístěních:

- Adresář nebo podadresáře aplikace

     Toto je nejběžnější umístění pro nasazení sestavení. Podadresáře kořenového adresáře aplikace může být založen na jazyku nebo jazykové verzi. Pokud sestavení obsahuje informace v atributu Culture, musí být v podadresáři v adresáři aplikace s názvem této jazykové verze.

- Globální mezipaměť sestavení (GAC).

     Jedná se o mezipaměť kódu v celém počítači, která je nainstalována bez ohledu na to, kde je nainstalován modul CLR (Common Language Runtime). Ve většině případů, pokud máte v úmyslu sdílet sestavení s více aplikacemi, je nutné jej nasadit do globální mezipaměti sestavení (GAC).

- Na serveru HTTP.

     Sestavení nasazené na serveru HTTP musí mít silný název; odkazujete na sestavení v oddílu základu kódu konfiguračního souboru aplikace.

## <a name="see-also"></a>Viz také:

- [Vytváření sestavení](create.md)
- [Globální mezipaměť sestavení](../../framework/app-domains/gac.md)
- [Způsob, jakým modul runtime vyhledává sestavení](../../framework/deployment/how-the-runtime-locates-assemblies.md)
