---
title: "Kolekce schématu rozhraní ODBC"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: b8c31f4e8b1463c184c9a8ff1cf64808783f030d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="c6952-102">Kolekce schématu rozhraní ODBC</span><span class="sxs-lookup"><span data-stu-id="c6952-102">ODBC Schema Collections</span></span>
<span data-ttu-id="c6952-103">Tato část popisuje podporu kolekci schématu pro ovladače ODBC pro Microsoft SQL Server, Oracle a Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="c6952-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="c6952-104">Ovladač ODBC Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="c6952-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="c6952-105">Ovladač ODBC Microsoft SQL Server podporuje následující kolekce konkrétní schématu kromě běžných kolekcemi schémat:</span><span class="sxs-lookup"><span data-stu-id="c6952-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="c6952-106">Tabulky</span><span class="sxs-lookup"><span data-stu-id="c6952-106">Tables</span></span>  
  
-   <span data-ttu-id="c6952-107">Indexy</span><span class="sxs-lookup"><span data-stu-id="c6952-107">Indexes</span></span>  
  
-   <span data-ttu-id="c6952-108">Sloupce</span><span class="sxs-lookup"><span data-stu-id="c6952-108">Columns</span></span>  
  
-   <span data-ttu-id="c6952-109">Procedury</span><span class="sxs-lookup"><span data-stu-id="c6952-109">Procedures</span></span>  
  
-   <span data-ttu-id="c6952-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="c6952-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="c6952-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="c6952-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="c6952-112">zobrazení</span><span class="sxs-lookup"><span data-stu-id="c6952-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="c6952-113">Tabulky a zobrazení</span><span class="sxs-lookup"><span data-stu-id="c6952-113">Tables and Views</span></span>  
  
|<span data-ttu-id="c6952-114">columnName</span><span class="sxs-lookup"><span data-stu-id="c6952-114">ColumnName</span></span>|<span data-ttu-id="c6952-115">Datový typ</span><span class="sxs-lookup"><span data-stu-id="c6952-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c6952-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="c6952-116">TABLE_CAT</span></span>|<span data-ttu-id="c6952-117">String</span><span class="sxs-lookup"><span data-stu-id="c6952-117">String</span></span>|  
|<span data-ttu-id="c6952-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="c6952-118">TABLE_SCHEM</span></span>|<span data-ttu-id="c6952-119">String</span><span class="sxs-lookup"><span data-stu-id="c6952-119">String</span></span>|  
|<span data-ttu-id="c6952-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6952-120">TABLE_NAME</span></span>|<span data-ttu-id="c6952-121">String</span><span class="sxs-lookup"><span data-stu-id="c6952-121">String</span></span>|  
|<span data-ttu-id="c6952-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6952-122">TABLE_TYPE</span></span>|<span data-ttu-id="c6952-123">String</span><span class="sxs-lookup"><span data-stu-id="c6952-123">String</span></span>|  
|<span data-ttu-id="c6952-124">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="c6952-124">REMARKS</span></span>|<span data-ttu-id="c6952-125">String</span><span class="sxs-lookup"><span data-stu-id="c6952-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="c6952-126">Indexy</span><span class="sxs-lookup"><span data-stu-id="c6952-126">Indexes</span></span>  
  
|<span data-ttu-id="c6952-127">columnName</span><span class="sxs-lookup"><span data-stu-id="c6952-127">ColumnName</span></span>|<span data-ttu-id="c6952-128">Datový typ</span><span class="sxs-lookup"><span data-stu-id="c6952-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c6952-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="c6952-129">TABLE_CAT</span></span>|<span data-ttu-id="c6952-130">String</span><span class="sxs-lookup"><span data-stu-id="c6952-130">String</span></span>|  
|<span data-ttu-id="c6952-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="c6952-131">TABLE_SCHEM</span></span>|<span data-ttu-id="c6952-132">String</span><span class="sxs-lookup"><span data-stu-id="c6952-132">String</span></span>|  
|<span data-ttu-id="c6952-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6952-133">TABLE_NAME</span></span>|<span data-ttu-id="c6952-134">String</span><span class="sxs-lookup"><span data-stu-id="c6952-134">String</span></span>|  
|<span data-ttu-id="c6952-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="c6952-135">NON_UNIQUE</span></span>|<span data-ttu-id="c6952-136">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-136">Int16</span></span>|  
|<span data-ttu-id="c6952-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="c6952-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="c6952-138">String</span><span class="sxs-lookup"><span data-stu-id="c6952-138">String</span></span>|  
|<span data-ttu-id="c6952-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="c6952-139">INDEX_NAME</span></span>|<span data-ttu-id="c6952-140">String</span><span class="sxs-lookup"><span data-stu-id="c6952-140">String</span></span>|  
|<span data-ttu-id="c6952-141">TYP</span><span class="sxs-lookup"><span data-stu-id="c6952-141">TYPE</span></span>|<span data-ttu-id="c6952-142">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-142">Int16</span></span>|  
|<span data-ttu-id="c6952-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="c6952-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="c6952-144">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-144">Int16</span></span>|  
|<span data-ttu-id="c6952-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c6952-145">COLUMN_NAME</span></span>|<span data-ttu-id="c6952-146">String</span><span class="sxs-lookup"><span data-stu-id="c6952-146">String</span></span>|  
|<span data-ttu-id="c6952-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="c6952-147">ASC_OR_DESC</span></span>|<span data-ttu-id="c6952-148">String</span><span class="sxs-lookup"><span data-stu-id="c6952-148">String</span></span>|  
|<span data-ttu-id="c6952-149">CARDINATLITY</span><span class="sxs-lookup"><span data-stu-id="c6952-149">CARDINATLITY</span></span>|<span data-ttu-id="c6952-150">Int32</span><span class="sxs-lookup"><span data-stu-id="c6952-150">Int32</span></span>|  
|<span data-ttu-id="c6952-151">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="c6952-151">PAGES</span></span>|<span data-ttu-id="c6952-152">Int32</span><span class="sxs-lookup"><span data-stu-id="c6952-152">Int32</span></span>|  
|<span data-ttu-id="c6952-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="c6952-153">FILTER_CONDITION</span></span>|<span data-ttu-id="c6952-154">String</span><span class="sxs-lookup"><span data-stu-id="c6952-154">String</span></span>|  
|<span data-ttu-id="c6952-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c6952-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="c6952-156">String</span><span class="sxs-lookup"><span data-stu-id="c6952-156">String</span></span>|  
|<span data-ttu-id="c6952-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6952-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="c6952-158">Byte</span><span class="sxs-lookup"><span data-stu-id="c6952-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="c6952-159">Sloupce</span><span class="sxs-lookup"><span data-stu-id="c6952-159">Columns</span></span>  
  
|<span data-ttu-id="c6952-160">columnName</span><span class="sxs-lookup"><span data-stu-id="c6952-160">ColumnName</span></span>|<span data-ttu-id="c6952-161">Datový typ</span><span class="sxs-lookup"><span data-stu-id="c6952-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c6952-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="c6952-162">TABLE_CAT</span></span>|<span data-ttu-id="c6952-163">String</span><span class="sxs-lookup"><span data-stu-id="c6952-163">String</span></span>|  
|<span data-ttu-id="c6952-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="c6952-164">TABLE_SCHEM</span></span>|<span data-ttu-id="c6952-165">String</span><span class="sxs-lookup"><span data-stu-id="c6952-165">String</span></span>|  
|<span data-ttu-id="c6952-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6952-166">TABLE_NAME</span></span>|<span data-ttu-id="c6952-167">String</span><span class="sxs-lookup"><span data-stu-id="c6952-167">String</span></span>|  
|<span data-ttu-id="c6952-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c6952-168">COLUMN_NAME</span></span>|<span data-ttu-id="c6952-169">String</span><span class="sxs-lookup"><span data-stu-id="c6952-169">String</span></span>|  
|<span data-ttu-id="c6952-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6952-170">DATA_TYPE</span></span>|<span data-ttu-id="c6952-171">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-171">Int16</span></span>|  
|<span data-ttu-id="c6952-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6952-172">TYPE_NAME</span></span>|<span data-ttu-id="c6952-173">String</span><span class="sxs-lookup"><span data-stu-id="c6952-173">String</span></span>|  
|<span data-ttu-id="c6952-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="c6952-174">COLUMN_SIZE</span></span>|<span data-ttu-id="c6952-175">Int32</span><span class="sxs-lookup"><span data-stu-id="c6952-175">Int32</span></span>|  
|<span data-ttu-id="c6952-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="c6952-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="c6952-177">Int32</span><span class="sxs-lookup"><span data-stu-id="c6952-177">Int32</span></span>|  
|<span data-ttu-id="c6952-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="c6952-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="c6952-179">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-179">Int16</span></span>|  
|<span data-ttu-id="c6952-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="c6952-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="c6952-181">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-181">Int16</span></span>|  
|<span data-ttu-id="c6952-182">S MOŽNOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="c6952-182">NULLABLE</span></span>|<span data-ttu-id="c6952-183">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-183">Int16</span></span>|  
|<span data-ttu-id="c6952-184">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="c6952-184">REMARKS</span></span>|<span data-ttu-id="c6952-185">String</span><span class="sxs-lookup"><span data-stu-id="c6952-185">String</span></span>|  
|<span data-ttu-id="c6952-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="c6952-186">COLUMN_DEF</span></span>|<span data-ttu-id="c6952-187">String</span><span class="sxs-lookup"><span data-stu-id="c6952-187">String</span></span>|  
|<span data-ttu-id="c6952-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6952-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="c6952-189">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-189">Int16</span></span>|  
|<span data-ttu-id="c6952-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="c6952-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="c6952-191">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-191">Int16</span></span>|  
|<span data-ttu-id="c6952-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="c6952-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="c6952-193">Int32</span><span class="sxs-lookup"><span data-stu-id="c6952-193">Int32</span></span>|  
|<span data-ttu-id="c6952-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="c6952-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="c6952-195">Int32</span><span class="sxs-lookup"><span data-stu-id="c6952-195">Int32</span></span>|  
|<span data-ttu-id="c6952-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="c6952-196">IS_NULLABLE</span></span>|<span data-ttu-id="c6952-197">String</span><span class="sxs-lookup"><span data-stu-id="c6952-197">String</span></span>|  
|<span data-ttu-id="c6952-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c6952-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="c6952-199">String</span><span class="sxs-lookup"><span data-stu-id="c6952-199">String</span></span>|  
|<span data-ttu-id="c6952-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c6952-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="c6952-201">String</span><span class="sxs-lookup"><span data-stu-id="c6952-201">String</span></span>|  
|<span data-ttu-id="c6952-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6952-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="c6952-203">Byte</span><span class="sxs-lookup"><span data-stu-id="c6952-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="c6952-204">Procedury</span><span class="sxs-lookup"><span data-stu-id="c6952-204">Procedures</span></span>  
  
|<span data-ttu-id="c6952-205">columnName</span><span class="sxs-lookup"><span data-stu-id="c6952-205">ColumnName</span></span>|<span data-ttu-id="c6952-206">Datový typ</span><span class="sxs-lookup"><span data-stu-id="c6952-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c6952-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="c6952-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="c6952-208">String</span><span class="sxs-lookup"><span data-stu-id="c6952-208">String</span></span>|  
|<span data-ttu-id="c6952-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="c6952-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="c6952-210">String</span><span class="sxs-lookup"><span data-stu-id="c6952-210">String</span></span>|  
|<span data-ttu-id="c6952-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6952-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="c6952-212">String</span><span class="sxs-lookup"><span data-stu-id="c6952-212">String</span></span>|  
|<span data-ttu-id="c6952-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="c6952-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="c6952-214">Int32</span><span class="sxs-lookup"><span data-stu-id="c6952-214">Int32</span></span>|  
|<span data-ttu-id="c6952-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="c6952-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="c6952-216">Int32</span><span class="sxs-lookup"><span data-stu-id="c6952-216">Int32</span></span>|  
|<span data-ttu-id="c6952-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="c6952-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="c6952-218">Int32</span><span class="sxs-lookup"><span data-stu-id="c6952-218">Int32</span></span>|  
|<span data-ttu-id="c6952-219">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="c6952-219">REMARKS</span></span>|<span data-ttu-id="c6952-220">String</span><span class="sxs-lookup"><span data-stu-id="c6952-220">String</span></span>|  
|<span data-ttu-id="c6952-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6952-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="c6952-222">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="c6952-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="c6952-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="c6952-224">columnName</span><span class="sxs-lookup"><span data-stu-id="c6952-224">ColumnName</span></span>|<span data-ttu-id="c6952-225">Datový typ</span><span class="sxs-lookup"><span data-stu-id="c6952-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c6952-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="c6952-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="c6952-227">String</span><span class="sxs-lookup"><span data-stu-id="c6952-227">String</span></span>|  
|<span data-ttu-id="c6952-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="c6952-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="c6952-229">String</span><span class="sxs-lookup"><span data-stu-id="c6952-229">String</span></span>|  
|<span data-ttu-id="c6952-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6952-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="c6952-231">String</span><span class="sxs-lookup"><span data-stu-id="c6952-231">String</span></span>|  
|<span data-ttu-id="c6952-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c6952-232">COLUMN_NAME</span></span>|<span data-ttu-id="c6952-233">String</span><span class="sxs-lookup"><span data-stu-id="c6952-233">String</span></span>|  
|<span data-ttu-id="c6952-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6952-234">COLUMN_TYPE</span></span>|<span data-ttu-id="c6952-235">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-235">Int16</span></span>|  
|<span data-ttu-id="c6952-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6952-236">DATA_TYPE</span></span>|<span data-ttu-id="c6952-237">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-237">Int16</span></span>|  
|<span data-ttu-id="c6952-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6952-238">TYPE_NAME</span></span>|<span data-ttu-id="c6952-239">String</span><span class="sxs-lookup"><span data-stu-id="c6952-239">String</span></span>|  
|<span data-ttu-id="c6952-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="c6952-240">COLUMN_SIZE</span></span>|<span data-ttu-id="c6952-241">Int32</span><span class="sxs-lookup"><span data-stu-id="c6952-241">Int32</span></span>|  
|<span data-ttu-id="c6952-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="c6952-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="c6952-243">Int32</span><span class="sxs-lookup"><span data-stu-id="c6952-243">Int32</span></span>|  
|<span data-ttu-id="c6952-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="c6952-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="c6952-245">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-245">Int16</span></span>|  
|<span data-ttu-id="c6952-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="c6952-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="c6952-247">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-247">Int16</span></span>|  
|<span data-ttu-id="c6952-248">S MOŽNOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="c6952-248">NULLABLE</span></span>|<span data-ttu-id="c6952-249">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-249">Int16</span></span>|  
|<span data-ttu-id="c6952-250">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="c6952-250">REMARKS</span></span>|<span data-ttu-id="c6952-251">String</span><span class="sxs-lookup"><span data-stu-id="c6952-251">String</span></span>|  
|<span data-ttu-id="c6952-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="c6952-252">COLUMN_DEF</span></span>|<span data-ttu-id="c6952-253">String</span><span class="sxs-lookup"><span data-stu-id="c6952-253">String</span></span>|  
|<span data-ttu-id="c6952-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6952-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="c6952-255">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-255">Int16</span></span>|  
|<span data-ttu-id="c6952-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="c6952-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="c6952-257">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-257">Int16</span></span>|  
|<span data-ttu-id="c6952-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="c6952-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="c6952-259">Int32</span><span class="sxs-lookup"><span data-stu-id="c6952-259">Int32</span></span>|  
|<span data-ttu-id="c6952-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="c6952-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="c6952-261">Int32</span><span class="sxs-lookup"><span data-stu-id="c6952-261">Int32</span></span>|  
|<span data-ttu-id="c6952-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="c6952-262">IS_NULLABLE</span></span>|<span data-ttu-id="c6952-263">String</span><span class="sxs-lookup"><span data-stu-id="c6952-263">String</span></span>|  
|<span data-ttu-id="c6952-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c6952-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="c6952-265">String</span><span class="sxs-lookup"><span data-stu-id="c6952-265">String</span></span>|  
|<span data-ttu-id="c6952-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c6952-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="c6952-267">String</span><span class="sxs-lookup"><span data-stu-id="c6952-267">String</span></span>|  
|<span data-ttu-id="c6952-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6952-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="c6952-269">Byte</span><span class="sxs-lookup"><span data-stu-id="c6952-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="c6952-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="c6952-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="c6952-271">columnName</span><span class="sxs-lookup"><span data-stu-id="c6952-271">ColumnName</span></span>|<span data-ttu-id="c6952-272">Datový typ</span><span class="sxs-lookup"><span data-stu-id="c6952-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c6952-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="c6952-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="c6952-274">String</span><span class="sxs-lookup"><span data-stu-id="c6952-274">String</span></span>|  
|<span data-ttu-id="c6952-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="c6952-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="c6952-276">String</span><span class="sxs-lookup"><span data-stu-id="c6952-276">String</span></span>|  
|<span data-ttu-id="c6952-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6952-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="c6952-278">String</span><span class="sxs-lookup"><span data-stu-id="c6952-278">String</span></span>|  
|<span data-ttu-id="c6952-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c6952-279">COLUMN_NAME</span></span>|<span data-ttu-id="c6952-280">String</span><span class="sxs-lookup"><span data-stu-id="c6952-280">String</span></span>|  
|<span data-ttu-id="c6952-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6952-281">COLUMN_TYPE</span></span>|<span data-ttu-id="c6952-282">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-282">Int16</span></span>|  
|<span data-ttu-id="c6952-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6952-283">DATA_TYPE</span></span>|<span data-ttu-id="c6952-284">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-284">Int16</span></span>|  
|<span data-ttu-id="c6952-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6952-285">TYPE_NAME</span></span>|<span data-ttu-id="c6952-286">String</span><span class="sxs-lookup"><span data-stu-id="c6952-286">String</span></span>|  
|<span data-ttu-id="c6952-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="c6952-287">COLUMN_SIZE</span></span>|<span data-ttu-id="c6952-288">Int32</span><span class="sxs-lookup"><span data-stu-id="c6952-288">Int32</span></span>|  
|<span data-ttu-id="c6952-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="c6952-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="c6952-290">Int32</span><span class="sxs-lookup"><span data-stu-id="c6952-290">Int32</span></span>|  
|<span data-ttu-id="c6952-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="c6952-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="c6952-292">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-292">Int16</span></span>|  
|<span data-ttu-id="c6952-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="c6952-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="c6952-294">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-294">Int16</span></span>|  
|<span data-ttu-id="c6952-295">S MOŽNOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="c6952-295">NULLABLE</span></span>|<span data-ttu-id="c6952-296">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-296">Int16</span></span>|  
|<span data-ttu-id="c6952-297">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="c6952-297">REMARKS</span></span>|<span data-ttu-id="c6952-298">String</span><span class="sxs-lookup"><span data-stu-id="c6952-298">String</span></span>|  
|<span data-ttu-id="c6952-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="c6952-299">COLUMN_DEF</span></span>|<span data-ttu-id="c6952-300">String</span><span class="sxs-lookup"><span data-stu-id="c6952-300">String</span></span>|  
|<span data-ttu-id="c6952-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6952-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="c6952-302">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-302">Int16</span></span>|  
|<span data-ttu-id="c6952-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="c6952-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="c6952-304">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-304">Int16</span></span>|  
|<span data-ttu-id="c6952-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="c6952-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="c6952-306">Int32</span><span class="sxs-lookup"><span data-stu-id="c6952-306">Int32</span></span>|  
|<span data-ttu-id="c6952-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="c6952-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="c6952-308">Int32</span><span class="sxs-lookup"><span data-stu-id="c6952-308">Int32</span></span>|  
|<span data-ttu-id="c6952-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="c6952-309">IS_NULLABLE</span></span>|<span data-ttu-id="c6952-310">String</span><span class="sxs-lookup"><span data-stu-id="c6952-310">String</span></span>|  
|<span data-ttu-id="c6952-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c6952-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="c6952-312">String</span><span class="sxs-lookup"><span data-stu-id="c6952-312">String</span></span>|  
|<span data-ttu-id="c6952-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c6952-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="c6952-314">String</span><span class="sxs-lookup"><span data-stu-id="c6952-314">String</span></span>|  
|<span data-ttu-id="c6952-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6952-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="c6952-316">Byte</span><span class="sxs-lookup"><span data-stu-id="c6952-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="c6952-317">Ovladač ODBC Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="c6952-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="c6952-318">Ovladač ODBC Microsoft SQL Server Oracle podporuje následující kolekce konkrétní schématu kromě běžných kolekcemi schémat:</span><span class="sxs-lookup"><span data-stu-id="c6952-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="c6952-319">Tabulky</span><span class="sxs-lookup"><span data-stu-id="c6952-319">Tables</span></span>  
  
-   <span data-ttu-id="c6952-320">Sloupce</span><span class="sxs-lookup"><span data-stu-id="c6952-320">Columns</span></span>  
  
-   <span data-ttu-id="c6952-321">Procedury</span><span class="sxs-lookup"><span data-stu-id="c6952-321">Procedures</span></span>  
  
-   <span data-ttu-id="c6952-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="c6952-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="c6952-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="c6952-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="c6952-324">zobrazení</span><span class="sxs-lookup"><span data-stu-id="c6952-324">Views</span></span>  
  
-   <span data-ttu-id="c6952-325">Indexy</span><span class="sxs-lookup"><span data-stu-id="c6952-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="c6952-326">Tabulky a zobrazení</span><span class="sxs-lookup"><span data-stu-id="c6952-326">Tables and Views</span></span>  
  
|<span data-ttu-id="c6952-327">columnName</span><span class="sxs-lookup"><span data-stu-id="c6952-327">ColumnName</span></span>|<span data-ttu-id="c6952-328">Datový typ</span><span class="sxs-lookup"><span data-stu-id="c6952-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c6952-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="c6952-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="c6952-330">String</span><span class="sxs-lookup"><span data-stu-id="c6952-330">String</span></span>|  
|<span data-ttu-id="c6952-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="c6952-331">TABLE_OWNER</span></span>|<span data-ttu-id="c6952-332">String</span><span class="sxs-lookup"><span data-stu-id="c6952-332">String</span></span>|  
|<span data-ttu-id="c6952-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6952-333">TABLE_NAME</span></span>|<span data-ttu-id="c6952-334">String</span><span class="sxs-lookup"><span data-stu-id="c6952-334">String</span></span>|  
|<span data-ttu-id="c6952-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6952-335">TABLE_TYPE</span></span>|<span data-ttu-id="c6952-336">String</span><span class="sxs-lookup"><span data-stu-id="c6952-336">String</span></span>|  
|<span data-ttu-id="c6952-337">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="c6952-337">REMARKS</span></span>|<span data-ttu-id="c6952-338">String</span><span class="sxs-lookup"><span data-stu-id="c6952-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="c6952-339">Sloupce</span><span class="sxs-lookup"><span data-stu-id="c6952-339">Columns</span></span>  
  
|<span data-ttu-id="c6952-340">columnName</span><span class="sxs-lookup"><span data-stu-id="c6952-340">ColumnName</span></span>|<span data-ttu-id="c6952-341">Datový typ</span><span class="sxs-lookup"><span data-stu-id="c6952-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c6952-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="c6952-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="c6952-343">String</span><span class="sxs-lookup"><span data-stu-id="c6952-343">String</span></span>|  
|<span data-ttu-id="c6952-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="c6952-344">TABLE_OWNER</span></span>|<span data-ttu-id="c6952-345">String</span><span class="sxs-lookup"><span data-stu-id="c6952-345">String</span></span>|  
|<span data-ttu-id="c6952-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6952-346">TABLE_NAME</span></span>|<span data-ttu-id="c6952-347">String</span><span class="sxs-lookup"><span data-stu-id="c6952-347">String</span></span>|  
|<span data-ttu-id="c6952-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c6952-348">COLUMN_NAME</span></span>|<span data-ttu-id="c6952-349">String</span><span class="sxs-lookup"><span data-stu-id="c6952-349">String</span></span>|  
|<span data-ttu-id="c6952-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6952-350">DATA_TYPE</span></span>|<span data-ttu-id="c6952-351">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-351">Int16</span></span>|  
|<span data-ttu-id="c6952-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6952-352">TYPE_NAME</span></span>|<span data-ttu-id="c6952-353">String</span><span class="sxs-lookup"><span data-stu-id="c6952-353">String</span></span>|  
|<span data-ttu-id="c6952-354">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="c6952-354">PRECISION</span></span>|<span data-ttu-id="c6952-355">Int32</span><span class="sxs-lookup"><span data-stu-id="c6952-355">Int32</span></span>|  
|<span data-ttu-id="c6952-356">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="c6952-356">LENGTH</span></span>|<span data-ttu-id="c6952-357">Int32</span><span class="sxs-lookup"><span data-stu-id="c6952-357">Int32</span></span>|  
|<span data-ttu-id="c6952-358">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="c6952-358">SCALE</span></span>|<span data-ttu-id="c6952-359">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-359">Int16</span></span>|  
|<span data-ttu-id="c6952-360">ZÁKLAD –</span><span class="sxs-lookup"><span data-stu-id="c6952-360">RADIX</span></span>|<span data-ttu-id="c6952-361">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-361">Int16</span></span>|  
|<span data-ttu-id="c6952-362">S MOŽNOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="c6952-362">NULLABLE</span></span>|<span data-ttu-id="c6952-363">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-363">Int16</span></span>|  
|<span data-ttu-id="c6952-364">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="c6952-364">REMARKS</span></span>|<span data-ttu-id="c6952-365">String</span><span class="sxs-lookup"><span data-stu-id="c6952-365">String</span></span>|  
|<span data-ttu-id="c6952-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="c6952-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="c6952-367">Int32</span><span class="sxs-lookup"><span data-stu-id="c6952-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="c6952-368">Procedury</span><span class="sxs-lookup"><span data-stu-id="c6952-368">Procedures</span></span>  
  
|<span data-ttu-id="c6952-369">columnName</span><span class="sxs-lookup"><span data-stu-id="c6952-369">ColumnName</span></span>|<span data-ttu-id="c6952-370">Datový typ</span><span class="sxs-lookup"><span data-stu-id="c6952-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c6952-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="c6952-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="c6952-372">String</span><span class="sxs-lookup"><span data-stu-id="c6952-372">String</span></span>|  
|<span data-ttu-id="c6952-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="c6952-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="c6952-374">String</span><span class="sxs-lookup"><span data-stu-id="c6952-374">String</span></span>|  
|<span data-ttu-id="c6952-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6952-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="c6952-376">String</span><span class="sxs-lookup"><span data-stu-id="c6952-376">String</span></span>|  
|<span data-ttu-id="c6952-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="c6952-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="c6952-378">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-378">Int16</span></span>|  
|<span data-ttu-id="c6952-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="c6952-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="c6952-380">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-380">Int16</span></span>|  
|<span data-ttu-id="c6952-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="c6952-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="c6952-382">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-382">Int16</span></span>|  
|<span data-ttu-id="c6952-383">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="c6952-383">REMARKS</span></span>|<span data-ttu-id="c6952-384">String</span><span class="sxs-lookup"><span data-stu-id="c6952-384">String</span></span>|  
|<span data-ttu-id="c6952-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6952-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="c6952-386">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="c6952-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="c6952-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="c6952-388">columnName</span><span class="sxs-lookup"><span data-stu-id="c6952-388">ColumnName</span></span>|<span data-ttu-id="c6952-389">Datový typ</span><span class="sxs-lookup"><span data-stu-id="c6952-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c6952-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="c6952-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="c6952-391">String</span><span class="sxs-lookup"><span data-stu-id="c6952-391">String</span></span>|  
|<span data-ttu-id="c6952-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="c6952-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="c6952-393">String</span><span class="sxs-lookup"><span data-stu-id="c6952-393">String</span></span>|  
|<span data-ttu-id="c6952-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6952-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="c6952-395">String</span><span class="sxs-lookup"><span data-stu-id="c6952-395">String</span></span>|  
|<span data-ttu-id="c6952-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c6952-396">COLUMN_NAME</span></span>|<span data-ttu-id="c6952-397">String</span><span class="sxs-lookup"><span data-stu-id="c6952-397">String</span></span>|  
|<span data-ttu-id="c6952-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6952-398">COLUMN_TYPE</span></span>|<span data-ttu-id="c6952-399">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-399">Int16</span></span>|  
|<span data-ttu-id="c6952-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6952-400">DATA_TYPE</span></span>|<span data-ttu-id="c6952-401">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-401">Int16</span></span>|  
|<span data-ttu-id="c6952-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6952-402">TYPE_NAME</span></span>|<span data-ttu-id="c6952-403">String</span><span class="sxs-lookup"><span data-stu-id="c6952-403">String</span></span>|  
|<span data-ttu-id="c6952-404">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="c6952-404">PRECISION</span></span>|<span data-ttu-id="c6952-405">Int32</span><span class="sxs-lookup"><span data-stu-id="c6952-405">Int32</span></span>|  
|<span data-ttu-id="c6952-406">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="c6952-406">LENGTH</span></span>|<span data-ttu-id="c6952-407">Int32</span><span class="sxs-lookup"><span data-stu-id="c6952-407">Int32</span></span>|  
|<span data-ttu-id="c6952-408">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="c6952-408">SCALE</span></span>|<span data-ttu-id="c6952-409">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-409">Int16</span></span>|  
|<span data-ttu-id="c6952-410">ZÁKLAD –</span><span class="sxs-lookup"><span data-stu-id="c6952-410">RADIX</span></span>|<span data-ttu-id="c6952-411">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-411">Int16</span></span>|  
|<span data-ttu-id="c6952-412">S MOŽNOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="c6952-412">NULLABLE</span></span>|<span data-ttu-id="c6952-413">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-413">Int16</span></span>|  
|<span data-ttu-id="c6952-414">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="c6952-414">REMARKS</span></span>|<span data-ttu-id="c6952-415">String</span><span class="sxs-lookup"><span data-stu-id="c6952-415">String</span></span>|  
|<span data-ttu-id="c6952-416">PŘETÍŽENÍ</span><span class="sxs-lookup"><span data-stu-id="c6952-416">OVERLOAD</span></span>|<span data-ttu-id="c6952-417">Int32</span><span class="sxs-lookup"><span data-stu-id="c6952-417">Int32</span></span>|  
|<span data-ttu-id="c6952-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="c6952-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="c6952-419">Int32</span><span class="sxs-lookup"><span data-stu-id="c6952-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="c6952-420">Ovladač ODBC Microsoft Jet</span><span class="sxs-lookup"><span data-stu-id="c6952-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="c6952-421">Ovladač ODBC Microsoft Jet podporuje následující kolekce konkrétní schématu kromě běžných kolekcemi schémat:</span><span class="sxs-lookup"><span data-stu-id="c6952-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="c6952-422">Tabulky</span><span class="sxs-lookup"><span data-stu-id="c6952-422">Tables</span></span>  
  
-   <span data-ttu-id="c6952-423">Indexy</span><span class="sxs-lookup"><span data-stu-id="c6952-423">Indexes</span></span>  
  
-   <span data-ttu-id="c6952-424">Sloupce</span><span class="sxs-lookup"><span data-stu-id="c6952-424">Columns</span></span>  
  
-   <span data-ttu-id="c6952-425">Procedury</span><span class="sxs-lookup"><span data-stu-id="c6952-425">Procedures</span></span>  
  
-   <span data-ttu-id="c6952-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="c6952-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="c6952-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="c6952-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="c6952-428">zobrazení</span><span class="sxs-lookup"><span data-stu-id="c6952-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="c6952-429">Tabulky a zobrazení</span><span class="sxs-lookup"><span data-stu-id="c6952-429">Tables and Views</span></span>  
  
|<span data-ttu-id="c6952-430">columnName</span><span class="sxs-lookup"><span data-stu-id="c6952-430">ColumnName</span></span>|<span data-ttu-id="c6952-431">Datový typ</span><span class="sxs-lookup"><span data-stu-id="c6952-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c6952-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="c6952-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="c6952-433">String</span><span class="sxs-lookup"><span data-stu-id="c6952-433">String</span></span>|  
|<span data-ttu-id="c6952-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="c6952-434">TABLE_OWNER</span></span>|<span data-ttu-id="c6952-435">String</span><span class="sxs-lookup"><span data-stu-id="c6952-435">String</span></span>|  
|<span data-ttu-id="c6952-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6952-436">TABLE_NAME</span></span>|<span data-ttu-id="c6952-437">String</span><span class="sxs-lookup"><span data-stu-id="c6952-437">String</span></span>|  
|<span data-ttu-id="c6952-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6952-438">TABLE_TYPE</span></span>|<span data-ttu-id="c6952-439">String</span><span class="sxs-lookup"><span data-stu-id="c6952-439">String</span></span>|  
|<span data-ttu-id="c6952-440">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="c6952-440">REMARKS</span></span>|<span data-ttu-id="c6952-441">String</span><span class="sxs-lookup"><span data-stu-id="c6952-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="c6952-442">Sloupce</span><span class="sxs-lookup"><span data-stu-id="c6952-442">Columns</span></span>  
  
|<span data-ttu-id="c6952-443">columnName</span><span class="sxs-lookup"><span data-stu-id="c6952-443">ColumnName</span></span>|<span data-ttu-id="c6952-444">Datový typ</span><span class="sxs-lookup"><span data-stu-id="c6952-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c6952-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="c6952-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="c6952-446">String</span><span class="sxs-lookup"><span data-stu-id="c6952-446">String</span></span>|  
|<span data-ttu-id="c6952-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="c6952-447">TABLE_OWNER</span></span>|<span data-ttu-id="c6952-448">String</span><span class="sxs-lookup"><span data-stu-id="c6952-448">String</span></span>|  
|<span data-ttu-id="c6952-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6952-449">TABLE_NAME</span></span>|<span data-ttu-id="c6952-450">String</span><span class="sxs-lookup"><span data-stu-id="c6952-450">String</span></span>|  
|<span data-ttu-id="c6952-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c6952-451">COLUMN_NAME</span></span>|<span data-ttu-id="c6952-452">String</span><span class="sxs-lookup"><span data-stu-id="c6952-452">String</span></span>|  
|<span data-ttu-id="c6952-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6952-453">DATA_TYPE</span></span>|<span data-ttu-id="c6952-454">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-454">Int16</span></span>|  
|<span data-ttu-id="c6952-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6952-455">TYPE_NAME</span></span>|<span data-ttu-id="c6952-456">String</span><span class="sxs-lookup"><span data-stu-id="c6952-456">String</span></span>|  
|<span data-ttu-id="c6952-457">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="c6952-457">PRECISION</span></span>|<span data-ttu-id="c6952-458">Int32</span><span class="sxs-lookup"><span data-stu-id="c6952-458">Int32</span></span>|  
|<span data-ttu-id="c6952-459">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="c6952-459">LENGTH</span></span>|<span data-ttu-id="c6952-460">Int32</span><span class="sxs-lookup"><span data-stu-id="c6952-460">Int32</span></span>|  
|<span data-ttu-id="c6952-461">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="c6952-461">SCALE</span></span>|<span data-ttu-id="c6952-462">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-462">Int16</span></span>|  
|<span data-ttu-id="c6952-463">ZÁKLAD –</span><span class="sxs-lookup"><span data-stu-id="c6952-463">RADIX</span></span>|<span data-ttu-id="c6952-464">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-464">Int16</span></span>|  
|<span data-ttu-id="c6952-465">S MOŽNOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="c6952-465">NULLABLE</span></span>|<span data-ttu-id="c6952-466">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-466">Int16</span></span>|  
|<span data-ttu-id="c6952-467">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="c6952-467">REMARKS</span></span>|<span data-ttu-id="c6952-468">String</span><span class="sxs-lookup"><span data-stu-id="c6952-468">String</span></span>|  
|<span data-ttu-id="c6952-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="c6952-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="c6952-470">Int32</span><span class="sxs-lookup"><span data-stu-id="c6952-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="c6952-471">Procedury</span><span class="sxs-lookup"><span data-stu-id="c6952-471">Procedures</span></span>  
  
|<span data-ttu-id="c6952-472">columnName</span><span class="sxs-lookup"><span data-stu-id="c6952-472">ColumnName</span></span>|<span data-ttu-id="c6952-473">Datový typ</span><span class="sxs-lookup"><span data-stu-id="c6952-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c6952-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="c6952-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="c6952-475">String</span><span class="sxs-lookup"><span data-stu-id="c6952-475">String</span></span>|  
|<span data-ttu-id="c6952-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="c6952-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="c6952-477">String</span><span class="sxs-lookup"><span data-stu-id="c6952-477">String</span></span>|  
|<span data-ttu-id="c6952-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6952-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="c6952-479">String</span><span class="sxs-lookup"><span data-stu-id="c6952-479">String</span></span>|  
|<span data-ttu-id="c6952-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="c6952-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="c6952-481">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-481">Int16</span></span>|  
|<span data-ttu-id="c6952-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="c6952-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="c6952-483">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-483">Int16</span></span>|  
|<span data-ttu-id="c6952-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="c6952-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="c6952-485">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-485">Int16</span></span>|  
|<span data-ttu-id="c6952-486">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="c6952-486">REMARKS</span></span>|<span data-ttu-id="c6952-487">String</span><span class="sxs-lookup"><span data-stu-id="c6952-487">String</span></span>|  
|<span data-ttu-id="c6952-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6952-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="c6952-489">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="c6952-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="c6952-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="c6952-491">columnName</span><span class="sxs-lookup"><span data-stu-id="c6952-491">ColumnName</span></span>|<span data-ttu-id="c6952-492">Datový typ</span><span class="sxs-lookup"><span data-stu-id="c6952-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c6952-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="c6952-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="c6952-494">String</span><span class="sxs-lookup"><span data-stu-id="c6952-494">String</span></span>|  
|<span data-ttu-id="c6952-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="c6952-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="c6952-496">String</span><span class="sxs-lookup"><span data-stu-id="c6952-496">String</span></span>|  
|<span data-ttu-id="c6952-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6952-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="c6952-498">String</span><span class="sxs-lookup"><span data-stu-id="c6952-498">String</span></span>|  
|<span data-ttu-id="c6952-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c6952-499">COLUMN_NAME</span></span>|<span data-ttu-id="c6952-500">String</span><span class="sxs-lookup"><span data-stu-id="c6952-500">String</span></span>|  
|<span data-ttu-id="c6952-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6952-501">COLUMN_TYPE</span></span>|<span data-ttu-id="c6952-502">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-502">Int16</span></span>|  
|<span data-ttu-id="c6952-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6952-503">DATA_TYPE</span></span>|<span data-ttu-id="c6952-504">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-504">Int16</span></span>|  
|<span data-ttu-id="c6952-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6952-505">TYPE_NAME</span></span>|<span data-ttu-id="c6952-506">String</span><span class="sxs-lookup"><span data-stu-id="c6952-506">String</span></span>|  
|<span data-ttu-id="c6952-507">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="c6952-507">PRECISION</span></span>|<span data-ttu-id="c6952-508">Int32</span><span class="sxs-lookup"><span data-stu-id="c6952-508">Int32</span></span>|  
|<span data-ttu-id="c6952-509">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="c6952-509">LENGTH</span></span>|<span data-ttu-id="c6952-510">Int32</span><span class="sxs-lookup"><span data-stu-id="c6952-510">Int32</span></span>|  
|<span data-ttu-id="c6952-511">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="c6952-511">SCALE</span></span>|<span data-ttu-id="c6952-512">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-512">Int16</span></span>|  
|<span data-ttu-id="c6952-513">ZÁKLAD –</span><span class="sxs-lookup"><span data-stu-id="c6952-513">RADIX</span></span>|<span data-ttu-id="c6952-514">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-514">Int16</span></span>|  
|<span data-ttu-id="c6952-515">S MOŽNOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="c6952-515">NULLABLE</span></span>|<span data-ttu-id="c6952-516">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-516">Int16</span></span>|  
|<span data-ttu-id="c6952-517">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="c6952-517">REMARKS</span></span>|<span data-ttu-id="c6952-518">String</span><span class="sxs-lookup"><span data-stu-id="c6952-518">String</span></span>|  
|<span data-ttu-id="c6952-519">PŘETÍŽENÍ</span><span class="sxs-lookup"><span data-stu-id="c6952-519">OVERLOAD</span></span>|<span data-ttu-id="c6952-520">Int32</span><span class="sxs-lookup"><span data-stu-id="c6952-520">Int32</span></span>|  
|<span data-ttu-id="c6952-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="c6952-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="c6952-522">Int32</span><span class="sxs-lookup"><span data-stu-id="c6952-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="c6952-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="c6952-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="c6952-524">columnName</span><span class="sxs-lookup"><span data-stu-id="c6952-524">ColumnName</span></span>|<span data-ttu-id="c6952-525">Datový typ</span><span class="sxs-lookup"><span data-stu-id="c6952-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c6952-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="c6952-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="c6952-527">String</span><span class="sxs-lookup"><span data-stu-id="c6952-527">String</span></span>|  
|<span data-ttu-id="c6952-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="c6952-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="c6952-529">String</span><span class="sxs-lookup"><span data-stu-id="c6952-529">String</span></span>|  
|<span data-ttu-id="c6952-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6952-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="c6952-531">String</span><span class="sxs-lookup"><span data-stu-id="c6952-531">String</span></span>|  
|<span data-ttu-id="c6952-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c6952-532">COLUMN_NAME</span></span>|<span data-ttu-id="c6952-533">String</span><span class="sxs-lookup"><span data-stu-id="c6952-533">String</span></span>|  
|<span data-ttu-id="c6952-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6952-534">COLUMN_TYPE</span></span>|<span data-ttu-id="c6952-535">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-535">Int16</span></span>|  
|<span data-ttu-id="c6952-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6952-536">DATA_TYPE</span></span>|<span data-ttu-id="c6952-537">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-537">Int16</span></span>|  
|<span data-ttu-id="c6952-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6952-538">TYPE_NAME</span></span>|<span data-ttu-id="c6952-539">String</span><span class="sxs-lookup"><span data-stu-id="c6952-539">String</span></span>|  
|<span data-ttu-id="c6952-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="c6952-540">COLUMN_SIZE</span></span>|<span data-ttu-id="c6952-541">Int32</span><span class="sxs-lookup"><span data-stu-id="c6952-541">Int32</span></span>|  
|<span data-ttu-id="c6952-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="c6952-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="c6952-543">Int32</span><span class="sxs-lookup"><span data-stu-id="c6952-543">Int32</span></span>|  
|<span data-ttu-id="c6952-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="c6952-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="c6952-545">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-545">Int16</span></span>|  
|<span data-ttu-id="c6952-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="c6952-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="c6952-547">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-547">Int16</span></span>|  
|<span data-ttu-id="c6952-548">S MOŽNOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="c6952-548">NULLABLE</span></span>|<span data-ttu-id="c6952-549">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-549">Int16</span></span>|  
|<span data-ttu-id="c6952-550">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="c6952-550">REMARKS</span></span>|<span data-ttu-id="c6952-551">String</span><span class="sxs-lookup"><span data-stu-id="c6952-551">String</span></span>|  
|<span data-ttu-id="c6952-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="c6952-552">COLUMN_DEF</span></span>|<span data-ttu-id="c6952-553">String</span><span class="sxs-lookup"><span data-stu-id="c6952-553">String</span></span>|  
|<span data-ttu-id="c6952-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6952-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="c6952-555">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-555">Int16</span></span>|  
|<span data-ttu-id="c6952-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="c6952-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="c6952-557">Int16</span><span class="sxs-lookup"><span data-stu-id="c6952-557">Int16</span></span>|  
|<span data-ttu-id="c6952-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="c6952-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="c6952-559">Int32</span><span class="sxs-lookup"><span data-stu-id="c6952-559">Int32</span></span>|  
|<span data-ttu-id="c6952-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="c6952-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="c6952-561">Int32</span><span class="sxs-lookup"><span data-stu-id="c6952-561">Int32</span></span>|  
|<span data-ttu-id="c6952-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="c6952-562">IS_NULLABLE</span></span>|<span data-ttu-id="c6952-563">String</span><span class="sxs-lookup"><span data-stu-id="c6952-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c6952-564">Viz také</span><span class="sxs-lookup"><span data-stu-id="c6952-564">See Also</span></span>  
 [<span data-ttu-id="c6952-565">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="c6952-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
