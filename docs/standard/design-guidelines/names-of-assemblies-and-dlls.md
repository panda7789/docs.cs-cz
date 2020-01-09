---
title: Názvy sestavení a knihoven DLL
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
ms.openlocfilehash: eebccba0b923b04333f289a85330d190c31013ab
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709254"
---
# <a name="names-of-assemblies-and-dlls"></a>Názvy sestavení a knihoven DLL
Sestavení je jednotka nasazení a identita pro programy spravovaného kódu. Přestože sestavení mohou zahrnovat jeden nebo více souborů, obvykle sestavení mapuje 1:1 pomocí knihovny DLL. Proto tato část popisuje pouze konvence vytváření názvů knihoven DLL, které je možné namapovat na zásady vytváření názvů sestavení.  
  
 **✓ DO** zvolte názvy pro vaše sestavení knihovny DLL, které naznačují velké množství funkcí, jako je například System.Data.  
  
 Názvy sestavení a knihoven DLL nemusí odpovídat názvům oboru názvů, ale při pojmenování sestavení je vhodné použít název oboru názvů. Dobrým pravidlem obsluhy je pojmenování knihovny DLL na základě společné předpony oborů názvů obsažených v sestavení. Například sestavení se dvěma obory názvů, `MyCompany.MyTechnology.FirstFeature` a `MyCompany.MyTechnology.SecondFeature`, lze volat `MyCompany.MyTechnology.dll`.  
  
 **✓ CONSIDER** pojmenování knihovny DLL podle vzoru následující:  
  
 `<Company>.<Component>.dll`  
  
 kde `<Component>` obsahuje jednu nebo více klauzulí oddělených tečkou. Příklad:  
  
 `Litware.Controls.dll`.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Pokyny pro pojmenování](../../../docs/standard/design-guidelines/naming-guidelines.md)
