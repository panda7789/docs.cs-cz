---
title: "Změny v oboru názvů System.Uri v verze 2.0"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35883fe9-2d09-4d8b-80ca-cf23a941e459
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 906abbcbd3ec00e76d8c183f61828fb5135d9154
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="changes-to-the-systemuri-namespace-in-version-20"></a>Změny v oboru názvů System.Uri v verze 2.0
Bylo provedeno několik změn <xref:System.Uri?displayProperty=nameWithType> třídy. Tyto změny pevné nesprávné chování, rozšířeného použitelnost a rozšířené zabezpečení.  
  
## <a name="obsolete-and-deprecated-members"></a>Zastaralé a zastaralé členy  
 Konstruktory:  
  
-   Všechny konstruktory, které mají `dontEscape` parametr.  
  
 Metody:  
  
-   <xref:System.Uri.CheckSecurity%2A>  
  
-   <xref:System.Uri.Escape%2A>  
  
-   <xref:System.Uri.Canonicalize%2A>  
  
-   <xref:System.Uri.Parse%2A>  
  
-   <xref:System.Uri.IsReservedCharacter%2A>  
  
-   <xref:System.Uri.IsBadFileSystemCharacter%2A>  
  
-   <xref:System.Uri.IsExcludedCharacter%2A>  
  
-   <xref:System.Uri.EscapeString%2A>  
  
## <a name="changes"></a>Změny  
  
-   Pro schémata identifikátoru URI, které jsou známé nemá část dotazu (soubor, ftp a dalších) '?' znak je vždy uvozené a nepovažuje začátku <xref:System.Uri.Query%2A> část.  
  
-   Implicitní souboru identifikátory URI (ve tvaru "c:\directory\file@name.txt"), fragment znak (#) je vždy uvozené Pokud úplné unescaping se požaduje nebo <xref:System.Uri.LocalPath%2A> je `true`.  
  
-   Odebrala se podpora název hostitele UNC; byla přijata specifikace IDN pro představující mezinárodní názvy hostitelů.  
  
-   <xref:System.Uri.LocalPath%2A>vždy vrátí hodnotu úplně neuvozené řetězec.  
  
-   <xref:System.Uri.ToString%2A>není unescape uvozený '%', '?', nebo znakem '#'.  
  
-   <xref:System.Uri.Equals%2A>nyní zahrnuje <xref:System.Uri.Query%2A> část v kontrole rovnosti.  
  
-   Operátory "=="a"! =" jsou přepsat a propojit s <xref:System.Uri.Equals%2A> metoda.  
  
-   <xref:System.Uri.IsLoopback%2A>nyní vytvoří konzistentních výsledků.  
  
-   Identifikátor URI "`file:///path`" je už přeložit na "file://path".  
  
-   "#" teď považována za zakončením název hostitele. Tedy "http://consoto.com#fragment" teď převést na "http://contoso.com/#fragment".  
  
-   Chyby při kombinování základní identifikátor URI s fragment byl opraven.  
  
-   Chyby v <xref:System.Uri.HostNameType%2A> vyřešen.  
  
-   Chyby při analýze NNTP vyřešen.  
  
-   Identifikátor URI ve tvaru HTTP:contoso.com nyní vyhodí výjimku analýzy.  
  
-   Rozhraní Framework správně zpracovává informací o uživateli v identifikátoru URI.  
  
-   Identifikátor URI cesta komprese vyřešen tak, aby porušený identifikátor URI nelze procházet systému souborů výše kořenu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Uri?displayProperty=nameWithType>
