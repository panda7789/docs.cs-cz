---
title: Umístění sestavení
ms.date: 08/20/2019
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
ms.openlocfilehash: 0b84aba749625f0f86027cd9d09a5e9a2229a3f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73733123"
---
# <a name="assembly-location"></a>Umístění sestavení
Umístění sestavení určuje, zda jej běžný jazyk runtime může vyhledat při odkazování a může také určit, zda lze sestavení sdílet s jinými sestaveními. Sestavení můžete nasadit v následujících umístěních:

- Adresář nebo podadresáře aplikace.

     Toto je nejběžnější umístění pro nasazení sestavení. Podadresáře kořenového adresáře aplikace mohou být založeny na jazyku nebo jazykové verzi. Pokud má sestavení informace v atributu jazykové verze, musí být v podadresáři pod adresářem aplikace s názvem této jazykové verze.

- Globální mezipaměti sestavení.

     Jedná se o mezipaměť kódu celého počítače, která je nainstalována všude tam, kde je nainstalován a) běžný jazyk runtime. Ve většině případů, pokud máte v úmyslu sdílet sestavení s více aplikacemi, měli byste jej nasadit do globální mezipaměti sestavení.

- Na serveru HTTP.

     Sestavení nasazené na serveru HTTP musí mít silný název. přejdete na sestavení v části základu kódu konfiguračního souboru aplikace.

## <a name="see-also"></a>Viz také

- [Vytváření sestavení](create.md)
- [Globální mezipaměť sestavení](../../framework/app-domains/gac.md)
- [Jak runtime vyhledá sestavení](../../framework/deployment/how-the-runtime-locates-assemblies.md)
