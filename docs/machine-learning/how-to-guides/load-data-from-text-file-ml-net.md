---
title: Načtení dat z textového souboru pro machine learning zpracování – ML.NET
description: Objevte, jak načíst data z textového souboru pro použití v modelu strojového učení, vytváření, trénování a vyhodnocování s ML.NET
ms.date: 02/06/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 70c7ccdeaa27b78a412c2bc82f524d4bf42a740a
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56091705"
---
# <a name="load-data-from-a-text-file-for-machine-learning-processing---mlnet"></a>Načtení dat z textového souboru pro machine learning zpracování – ML.NET

`TextLoader` slouží k načtení dat z textových souborů. Je třeba zadat sloupců dat, jejich typy a jejich umístění v textovém souboru.

Všimněte si, že se nemusíte zajistit dokonalou přijatelné číst některé sloupce souboru, nebo stejný sloupec více než jednou.

[Příklad souboru](https://github.com/dotnet/machinelearning/blob/master/test/data/adult.tiny.with-schema.txt):

```console
Label   Workclass   education   marital-status
0   Private 11th    Never-married
0   Private HS-grad Married-civ-spouse
1   Local-gov   Assoc-acdm  Married-civ-spouse
1   Private Some-college    Married-civ-spouse
```

Chcete načíst data z textového souboru:

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Create the reader: define the data columns and where to find them in the text file.
var reader = mlContext.Data.CreateTextLoader(
    columns: new TextLoader.Column[]
    {
        // A boolean column depicting the 'target label'.
        new TextLoader.Column("IsOver50k",DataKind.BL,0),
        // Three text columns.
        new TextLoader.Column("WorkClass",DataKind.TX,1),
        new TextLoader.Column("Education",DataKind.TX,2),
        new TextLoader.Column("MaritalStatus",DataKind.TX,3)
    },
    hasHeader: true
);

// Now read the file (remember though, readers are lazy, so the actual reading will happen when the data is accessed).
var data = reader.Read(dataPath);
```