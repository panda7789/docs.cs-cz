---
title: Názvy sestavení a knihoven DLL
description: Přečtěte si pokyny pro pojmenovávání sestavení a knihovny DLL (Dynamic-Link Library). Sestavení může zahrnovat jeden nebo více souborů, ale obvykle mapuje 1:1 pomocí knihovny DLL.
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
ms.openlocfilehash: de7ce3ee774d4598521d7156d0d660c3fe30154c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594475"
---
# <a name="names-of-assemblies-and-dlls"></a>Názvy sestavení a knihoven DLL
Sestavení je jednotka nasazení a identita pro programy spravovaného kódu. Přestože sestavení mohou zahrnovat jeden nebo více souborů, obvykle sestavení mapuje 1:1 pomocí knihovny DLL. Proto tato část popisuje pouze konvence vytváření názvů knihoven DLL, které je možné namapovat na zásady vytváření názvů sestavení.

 ✔️ zvolit názvy pro knihovny DLL sestavení, které navrhují velké bloky funkčnosti, jako je System. data.

 Názvy sestavení a knihoven DLL nemusí odpovídat názvům oboru názvů, ale při pojmenování sestavení je vhodné použít název oboru názvů. Dobrým pravidlem obsluhy je pojmenování knihovny DLL na základě společné předpony oborů názvů obsažených v sestavení. Například sestavení se dvěma obory názvů `MyCompany.MyTechnology.FirstFeature` a, lze `MyCompany.MyTechnology.SecondFeature` volat `MyCompany.MyTechnology.dll` .

 ✔️ Zvažte pojmenování knihoven DLL podle následujícího vzoru:

 `<Company>.<Component>.dll`

 kde `<Component>` obsahuje jednu nebo více klauzulí oddělených tečkou. Například:

 `Litware.Controls.dll`.

 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také

- [Pokyny k návrhu architektury](index.md)
- [Pokyny pro pojmenování](naming-guidelines.md)
